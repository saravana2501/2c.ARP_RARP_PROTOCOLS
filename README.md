# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## NAME: SARAVANA KUMAR S
## REG NO.: 212224220090
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP
```
CLIENT:

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
```
SERVER:

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```


## OUPUT - ARP
![Screenshot 2025-03-19 111921](https://github.com/user-attachments/assets/5d9b4ac7-bc0d-4a44-b739-02536f586d2d)
![Screenshot 2025-03-19 111956](https://github.com/user-attachments/assets/06d72bc5-7e93-4b83-9a01-676f79bbf5bd)

## PROGRAM - RARP
```
CLIENT:
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
```
SERVER:
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP
![Screenshot 2025-03-19 113845](https://github.com/user-attachments/assets/d56f3949-9742-4e22-968f-98c8a4b9b7ec)
![Screenshot 2025-03-19 113914](https://github.com/user-attachments/assets/66329df0-4ba2-4119-a6de-42e0fba066cd)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
