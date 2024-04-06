# simple-network-file-system
## A simple client-server network file system (NFS) over a simulated disk.

YJ Simple Network File System 0.0.1 Documentation
Welcome! This is the official documentation for YJ SNFS (Simple Network File System) 0.0.1.

###### Configuration:
The YJ SNFS (Simple Network File System) must be run on a Linux environment due to complicated and lots of configuration requirements.
- The basic Linux environment is already set up for required packages, but if anything is not set up yet, then install it using command such as ‘sudo apt install -’.

Download the zip file (YJ-Simple-Network-File-System.zip) and extract in a directory in the Linux System.
- Extract the zip file.

###### Compilation:
- Once downloading and extracting the zipped file, under the directory ‘YJ-Simple-Network-File-System‘, do mouse right-click and click ‘Open in Terminal’.
- In the command, type in the ‘make’ and all the required executable files are generated.
- Next, open a Server port (e.g., 8080). Then the current terminal becomes the ‘Server’.
- In the same directory above of ‘YJ-Simple-Network-File-System‘, Open another terminal for ‘Client’. Then type in the the ‘./nfsclient’, IP address of the system, and the server port number, i.e., ‘./nfsclient 10.0.2.15:8080’. Then it opens the socket and connects to the SNFS server.
- Finally, it got connected to the SNFS server and it outputs the command ‘NFS>’, so that you can type in any system commands.

###### File System Commands:
- `mkdir <directory>` - Creates an empty subdirectory in the current directory.
- `ls` - List the contents of the current directory. Directories should have a '/' suffix such as 'myDir/'. Files do not have a suffix.
- `cd <directory>` - Change to specified directory. The directory must be a subdirectory in the current directory. No paths or ".." are allowed.
- `home` - Switch to the home directory.
- `rmdir <directory>` - Removes a subdirectory. The subdirectory must be empty.
- `create <filename>` - Creates an empty file of the filename in the current directory. An empty file consists of an inode and no data blocks.
- `append <filename> <data>` - Appends the data to the file. Data should be appended in a manner to first fill the last data block as much as possible and then allocating new block(s) ONLY if more space is needed. More information about the format of data files is described later.
- `stat <name>` - Displays stats for the given file or directory. The precise format is described later in the document.
- `cat <filename>` - Display the contents of the file to the screen. Print a newline when completed.
- `head <filename> <n>` - Display the first N bytes of the file to the screen. Print a newline when completed. (If N >= file size, print the whole file just as with the cat command.)
- `rm <filename>` - Remove a file from the directory, reclaim all of its blocks including its inode. Cannot remove directories.

###### Tutorial:
- Directory Creation using ‘mkdir’.
  * Example of creating directory ‘youngsun’, folder name ends with ‘/’. You can check this by listing ‘ls’.
File Creation using ‘create’
File writing using ‘append’.

###### References:
In the PA1 assignment notice, there are three useful resources below:
1.	Sun Microsystems. Network File System (NFS) 
https://www.geeksforgeeks.org/network-file-system-nfs/ 
2.	NFS based on Remote Procedure Calling (RPC). https://www.cs.fsu.edu/~engelen/courses/COP4610/lab4.html 
3.	Simple Client-Server NFS Implemented Over A Simulated Disk.  https://github.com/dmonaldo/simple-network-file-system
In below a brief summary of each of resource is given.

1. Network File System (NFS)
This reference provides information about the Network File System (NFS), a distributed file system developed by Sun Microsystems. Here's a breakdown of the key points:
•	**Introduction to Distributed File Systems**: Distributed file systems allow multiple client machines to access data stored on one or more servers. They facilitate easy sharing of data among clients, centralized administration, and security through securing the servers.
•	**Architecture**: The architecture of a distributed file system involves both client-side and server-side components. Client applications issue system calls to access files, which are then retrieved from the server. This process is transparent to the client application, making file access seamless.
•	**NFS**: Sun Microsystems developed the Network File System (NFS), one of the earliest successful distributed systems. NFSv2 was designed to enable simple and fast recovery from server crashes, crucial for multi-client and single-server network architectures.
•	**Stateless Protocol**: NFS implements a stateless protocol, meaning the server does not store any state information about client requests. This simplifies recovery from server crashes, as clients can retry requests if needed.
•	**File Handles**: NFS uses file handles to uniquely identify files or directories. File handles consist of a volume identifier, inode number, and generation number.
•	**File Attributes**: NFS tracks metadata of files, known as file attributes, including creation time, last modified, size, and ownership permissions.
•	**Protocol Messages**: NFSv2 defines several protocol messages for operations such as getting and setting file attributes, file lookup, reading, writing, creating, and removing files and directories.
•	**Client-Side Caching**: To improve performance, NFS employs client-side caching, where data and metadata read from the server are cached on the client. This reduces the time taken for subsequent accesses and improves efficiency.
Overall, this reference provides a comprehensive overview of NFS, including its architecture, protocol, and key features, which can be valuable for understanding distributed file systems and implementing similar systems in projects or applications.

2. NFS based on Remote Procedure Calling (RPC)
This document outlines a lab assignment focused on understanding the functioning of a simple network file system based on remote procedure calling (RPC) mechanism between a network file system client and a (stateless) network file system server. Here's a breakdown of the key points:
•	**RPC Classes**: The source code contains classes named RPC.h and RPC.cpp, which implement the RPC mechanism for communication between the client and the server.
•	**RPC Operations**: The RPC class provides methods for connecting to the server, disconnecting from the server, and making remote procedure calls.
•	**RPC Functionality**: The connect method establishes a connection with the server, the disconnect method terminates the connection, and the call method issues a command to the server and receives a response.
•	**Command Format**: The RPC class sends command messages to the server in a specific format, including the command itself, a block number, and block data.
•	**Supported Commands**: The RPC class supports several commands, such as querying the number of disk blocks, formatting the disk, reading data from the disk, writing data to the disk, creating files, removing files, and creating directories.
Overall, the assignment provides students with hands-on experience in developing and enhancing a network file system using RPC mechanism, along with understanding key concepts related to distributed file systems.

3. Simple Client-Server NFS Implemented Over A Simulated Disk
The provided information describes a simple client-server network file system (NFS) implemented over a simulated disk. Here's a breakdown of the key points:
•	**Structure**: 
-	**Client-Side Shell**: Processes NFS commands from the command line.
-	**Server-Side File System**: Provides an interface for NFS commands received from the client via TCP socket and sends back responses.
-	**Basic File System**: Low-level interface interacting with the disk.
-	**Disk**: Represents a "virtual" disk contained within a file.
-	**Client and Server**: Main programs for the NFS client and server.
•	**File System Commands**:
-	**mkdir <directory>**: Creates an empty subdirectory.
-	**ls**: Lists the contents of the current directory.
-	**cd <directory>**: Changes to the specified directory.
-	**home**: Switches to the home directory.
-	**rmdir <directory>**: Removes a subdirectory.
-	**create <filename>**: Creates an empty file.
-	**append <filename> <data>**: Appends data to the file.
-	**stat <name>**: Displays stats for the given file or directory.
-	**cat <filename>**: Displays the contents of the file.
-	**head <filename> <n>**: Displays the first N bytes of the file.
-	**rm <filename>**: Removes a file from the directory.
Overall, this description provides an overview of the structure of the network file system, its functionalities, contributions of team members, and an assessment of its functionality along with test cases. 

###### Project Management:
This program is managed by using GitHub. The address for the GitHub is: 
https://github.com/youngsunjang/Class_SDSU_ComputerNetwork
