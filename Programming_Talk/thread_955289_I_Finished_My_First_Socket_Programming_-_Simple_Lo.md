---
title: "I Finished My First Socket Programming - Simple Local Port Scanner! What Do You Think"
date: 2008-10-22
forum: Programming Talk
---

### Post by f.ben.isaac@gmail.com on 2008-10-22
Hello!

I wrote a program that scans ports in my local machine. It is not efficient, but i would like to know whether the algorithm is right or not - regardless of efficiency?

This program prints your local machine name & your local IP Address with the type of your address whether its IPv4 or IPv6. After that prompts you to enter the starting port & ending port. Go through a loop and try to connect to each port. If it connects, port is open. Otherwise, port is closed....

QUESTION: I'm just wondering why all ports show as Closed?!!! I tried to put ports from 1 to 3000, all closed! i think i have lots of ports open in my OS - i do not know - maybe! 
I tested this program under linux ubuntu...

Here is the code:

```

#include<iostream>
#include<string>
#include<sstream>
#include<sys/types.h>
#include<sys/socket.h>
#include<netdb.h>
#include<arpa/inet.h>
using namespace std;


struct addrinfo hints;      	//fill your host info - hints is input
struct addrinfo *results;	//gets your host info - results is output
char *pcName = new char[40];    //holds your pc name
string tempPort;                //holds ports temporarly
int startingPort;               //stores the starting range of port number
int status;                     //receives the status of your pc address
char currentPort[10];           //holds current port

//program description
void progDesc()
{
     cout<<"This is a simple port scanner, scan range of\n";
     cout<<"ports on your local machine...\n"<<endl;

}

//call host (local machine) name
void callHostName()
{
	size_t pcNameSize;     				  //holds size of the name
	int hostNameStatus; 				  //holds status of the function whether it succeeded or failed
	hostNameStatus = gethostname(pcName, pcNameSize); //gethostname grabs your pc name & pass it to pcName
	
	//make sure function host name returned successfully
	if(hostNameStatus == -1 )
	{
		cout<<"Error: could not locate your host name\n";
		exit(1);
	}

	//print machine name
	cout<<"Your Machine Name: ";
	cout<<pcName<<endl;
	cout<<endl;

	//deallocate memory
	//delete[] pcName; - i put it inside main()

}

//getaddrinfe locates your machine, more specific
//details of your host address is returned to results. 
void getAddrIn()
{

	status = getaddrinfo(pcName, currentPort, &hints, &results);

	if(status != 0)
	{
		fprintf(stderr, "getaddrinfo error: %s\n", gai_strerror(status));
		exit(1);
	}
}

//get local IP which is usually version 4
void grabLocalIP()
{
	//carries your local IP
	char ipString[INET6_ADDRSTRLEN];
	struct addrinfo *p;
	
	cout<<"IP Address for "<<pcName<<" is of type ";

	//print all your local IP Addresses
	for(p = results; p != NULL; p = p->ai_next)
	{
		void *addr;
		string ipVer;
		if(p->ai_family == AF_INET)
		{
			struct sockaddr_in *ipv4 = (struct sockaddr_in *)p->ai_addr;
			addr = &(ipv4->sin_addr);
			ipVer = "IPv4";

		}else{
			struct sockaddr_in6 *ipv6 = (struct sockaddr_in6 *)p->ai_addr;
			addr = &(ipv6->sin6_addr);
			ipVer = "IPv6";
		}

		inet_ntop(p->ai_family, addr, ipString, sizeof ipString);
		cout<<""<<ipVer<<": ";
		printf("%s\n", ipString);
		cout<<endl;
	}	
}

//convert a port from int to *char, so it can be passed into getaddrinfo()
//call this function before the loop starts
void convertPortsToString()
{
	//convert startingPort to string. After that, convert the string into *char...
	//string tempPort;  make it static 
	stringstream out;
	out<<startingPort;
	tempPort = out.str();    //tempPort carries startingPort in string format

	//convert tempPort to *char - currentPort going to be passed into getaddrinfo()
	//char currentPort[10];  - i made it static
	strcpy(currentPort, tempPort.c_str());

}

//convert a port from int to *char, so it can be passed into getaddrinfo()
//call this function at the bottom of the loop
void convertIncrementedPortsToString()
{
	//you have to declare out in every loop, otherwise the 
	//incremented ports will concatenated with the previous ports.
	stringstream out;
	out<<startingPort;
	tempPort = out.str();    		//tempPort carries startingPort in string format
	strcpy(currentPort, tempPort.c_str());  //convert the string to *char

}

//Run the program
int main()
{
	int endingPort;                 //stores the ending rage of port number

	system("clear");

	//tell user what program does
	progDesc();

	//grab the name of the local machine (host)
	callHostName();
	
	//set size of hints to zero
	memset(&hints, 0, sizeof hints);

	//fill some of your host address info
	hints.ai_family = AF_UNSPEC;
	hints.ai_socktype = SOCK_STREAM;

	//call getaddrinfo() to output to "results"
	//so you can grab the local IP from results
	getAddrIn();

	//grab your machine local IP
	grabLocalIP();

	//ask port range from user
	cout<<"Enter Starting Port: ";
	cin>>startingPort;

	cout<<"Enter Ending Port: ";
	cin>>endingPort;

	cout<<endl;

	cout<<"Start Checking: "<<endl;

	//convert a port from int to *char, so it can be passed into getaddrinfo()
	convertPortsToString();

	//check the status
	while(startingPort <= endingPort)
	{
		//call getaddrinfo()
		getAddrIn();

		//create a socket.
		int socketfd;
		socketfd = socket(results->ai_family, results->ai_socktype, results->ai_protocol);

		if(socketfd == -1 )
		{
			cout<<"Error: failed to create a socket.\n";
			return 2;
		}

		//connect to your own IP address in every loop with 
		//a new port, connect() will associate your socket
		//with the "current port number & your local IP address".
		int connectStatus;
		connectStatus = connect(socketfd, results->ai_addr, results->ai_addrlen);
	
		if(connectStatus == -1 )
		{
			cout<<"Port "<<currentPort<<" is Closed or Blocked.\n";
		}else{
			cout<<"Port "<<currentPort<<" is OPEN.\n";
		}

		close(socketfd);
	
		//move to the next port in the specified range
		startingPort++;

		/***convert the incremented port to *char***/
		convertIncrementedPortsToString();
	}

	//deallocate memory
	delete[] pcName;

	//free linkedlist of struct addrinfo *results 
	freeaddrinfo(results);

	return 0;
}


```

Output:

```

This is a simple port scanner, scan range of
ports on your local machine...

Your Machine Name: Toshiba-Laptop

IP Address for Toshiba-Laptop is of type IPv4: 127.0.1.1

Enter Starting Port: 1
Enter Ending Port: 5

Start Checking: 
Port 1 is Closed or Blocked.
Port 2 is Closed or Blocked.
Port 3 is Closed or Blocked.
Port 4 is Closed or Blocked.
Port 5 is Closed or Blocked.


```

Any help will be appreciated! The main algorithm is inside the while loop...

THANKS  :)

---

### Post by Rich78 on 2008-10-22
To test your open ports, run Nmap from a different machine against your machine.

I'm sure the problem you have is you can't scan localhost for open ports.

You could also run netstat which would show any active connections and so would five you an idea of open ports.

---

### Post by SeanHodges on 2008-10-23
You sure can scan localhost for open ports, but you might get a different output from when you scan from a remote machine... Running nmap as Rich78 suggested is a good idea because it will give you an idea of what output you should be expecting.

```
sudo apt-get install nmap
nmap localhost
```

Lots of ports will not be active (not necessarily closed, but no program will be listening on them). Depending on your installed services, you might find a few active ones like 22 (SSH), 139 (netbios), etc. Most will return the "is Closed or Blocked" message though.

---

### Post by dwhitney67 on 2008-10-23
A couple of weeks ago I posted on this forum a Socket library I had tinkered with over the past 5 years.  Using it, I came up with the program below just now.  It should be able to be used on the localhost (127.0.0.1) or on a remote host within the same network.

It does not display the wealth of information as in the OP's code, but it can be used to verify if a port is indeed open and accepting connections.

To compile the code:
```
g++ PortScanner.cpp -lSocket -lboost_thread -o portscanner
```

PortScanner.cpp:
[php]
#include <TCPClientSocket.h>
#include <iostream>
#include <string>
#include <vector>


void displayPort(unsigned short port);


int main()
{
  unsigned short startPort = 0;
  unsigned short endPort   = 0;
  std::string    host;

  std::cout << "Enter the start port number to use is scan: ";
  std::cin  >> startPort;
  std::cout << "Enter the end port number to use is scan:   ";
  std::cin  >> endPort;
  std::cout << "Hostname (or IP) of the system to search:   ";
  std::cin  >> host;

  std::vector<unsigned short> portsOpen;

  for (unsigned short port = startPort; port <= endPort; ++port)
  {
    try
    {
      TCPClientSocket client;
      client.Connect(host, port);
      portsOpen.push_back(port);
    }
    catch (std::exception& ex)
    {
    }
  }

  // print results
  if (portsOpen.size() > 0)
  {
    std::cout << "Open ports:" << std::endl;
    std::for_each(portsOpen.begin(), portsOpen.end(), displayPort);
  }
  else
  {
    std::cout << "No open ports found in the port-range given." << std::endl;
  }

  return 0;
}


void displayPort(unsigned short port)
{
  std::cout << "Port " << value << " is open and accepting connections." << std::endl;
}
[/php]

---

