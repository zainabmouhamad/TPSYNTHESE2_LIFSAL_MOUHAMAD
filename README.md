Introduction:
The goal of this work is to create a client program that allows file transfer using the TFTP protocol, which is used for OS installation, diskless workstations, and firmware updates. 
TFTP is a protocol used to transfer files.We downloaded a server for local use. 

Question 1:
In a file .c, there is command-line arguments in the gettftp and puttftp programs to retrieve request information (server and file).

Question 2:
For this part, we are using command to get the adress information of the server.

![terminal__q2](https://github.com/user-attachments/assets/958ac06c-1a67-475a-b696-94b42c478c39)

We are able to display the information of the server in the terminal


Question 3:
Socket reservation involves using socket() to create a network communication point with the server, then checking that the returned descriptor is valid (not -1).

In wireshark, we can see the communication between 127.0.0.1 and 127.0.0.53, with a protocol TFTP asking for a standart query and the destinator give a response to that query
![image](https://github.com/user-attachments/assets/ded5abe5-345a-4b5e-871a-534ea8174519)


Question 3:
We will use socket reservation that involves using socket() to create a network communication point with the server, then checking that the returned descriptor is valid (not -1).
We can see in the terminal that the socket is created:
![terminal_q3](https://github.com/user-attachments/assets/b357c4d5-beff-4da7-99b6-03ede9a4aed7)


Question 4 :
The goal of this part is to create an RRQ request.
RRQ and WRQ packets (opcodes 1 and 2 respectively) have the format shown in the figure below. So for this part we will have the value in the opcode.

![RFC_RRQ_WRQ](https://github.com/user-attachments/assets/cd53e6e5-be78-4d9e-a72a-2ef683973779)
 Octet mode is used to transfer a file that is in the 8-bit format of the machine from which the file is being transferred.
The first 2 bytes will have the value 1, then the 2nd position of the trame will have the filename, the 3rd position will have 1 bytes of value 0. the 4th position will have the mode 'octet' and a 1 byte of value 0.

 After creating and sending a rrq we have this in the terminal:
 
![thumbnail_image](https://github.com/user-attachments/assets/f1d6d8c2-ec79-4fd4-a048-4037a289a1ef)

Then we will receive a file of a single Data and receive its acknowledgment (ACK)

![Capture du 2024-12-17 11-23-40](https://github.com/user-attachments/assets/fe9cb9e0-749b-4796-b2cd-4edba968db36)
DATA packets (opcode = 3) have a block number and data field. The block numbers on data packets begin with one and increase by one for each new block of data. 

![Capture du 2024-12-17 11-25-08](https://github.com/user-attachments/assets/fb466a99-6d8c-4083-b220-c59beb4eb111)
Figure 5-3 depicts an ACK packet; the opcode is 4.The  block  number  in  ACK echoes the block number of the DATA packet beingacknowledged.

