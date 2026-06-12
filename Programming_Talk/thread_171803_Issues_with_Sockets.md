---
title: "Issues with Sockets"
date: 2006-05-07
forum: Programming Talk
---

### Post by Mitch.Pitt on 2006-05-07
Hey everyone, I am working on a school project that requires the use of sockets.  I have a client and server program developed.  So I will load the server app and it runs fine.  But when I start a client, it will act like I sent something through the socket to the server.  

So the server will just print out garbage variables when I load the client app.  I've tried this on another computer and it works perfect, so there's an issue with my computer.  Are there specific libraries that are need for sockets?

---

### Post by yaaarrrgg on 2006-05-07
what language are you using? (c?)
also, what is the platform of the computer that works?  (ubuntu linux?)

I would think for most languages, the socket libraries should be installed by default.

---

### Post by Mitch.Pitt on 2006-05-07
[QUOTE=yaaarrrgg]what language are you using? (c?)
also, what is the platform of the computer that works?  (ubuntu linux?)

I would think for most languages, the socket libraries should be installed by default.[/QUOTE]


Language is C++ and in Ubuntu Linux.  I talked to another guy who uses Ubuntu and he can get sockets to work.  The school computers use Fedora.  Both OSs are similar.  I thought it would be a default thing too, but I don't understand why the Read() function on the Server doesn't wait for a write() function from the client.  Very very odd.

---

### Post by LordHunter317 on 2006-05-07
It's because you have a bug in your program, almost certainly.  Post your code.

---

### Post by Mitch.Pitt on 2006-05-07
[QUOTE=LordHunter317]It's because you have a bug in your program, almost certainly.  Post your code.[/QUOTE]

It's not a bug.  It will work on the linux machines at my school. But when I try it at home it craps out.

---

### Post by LordHunter317 on 2006-05-07
Which clearly means it's a bug you're just not triggering all the time.  Sounds like a race condition of sorts.  Post your code.

---

### Post by yaaarrrgg on 2006-05-07
[QUOTE=Mitch.Pitt]It's not a bug.  It will work on the linux machines at my school. But when I try it at home it craps out.[/QUOTE]

Even if there isn't a bug, it wouldn't hurt to run the code past the c++ gurus here.  The more info you can provide, the better.  Might give more insight into the problem, like what libraries you are calling...

---

### Post by Mitch.Pitt on 2006-05-07
Here is the client code...  If you have questions I can explain it

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <iostream>

using namespace std;

struct user_validation
{
	char uname[10];
	char password[10];
	char account_number[8];
	char isvalid[2];
	char account_type[2]; //'C' for Customer, 'T' for Teller
};

struct bnb_cust_data
{
	int bank_code;
	int bank_result_code;
	char bank_user_name[10];
	char bank_user_password[10];
	char bank_customer_name[30];
	char bank_account_number[8];
	char bank_account_type;
	float bank_account_total;
	float bank_amount;
};

int main()
{
	int client_socket;
	int len;
	//  Network form of address structure
	struct sockaddr_in address;
	struct user_validation u_valid;
	struct bnb_cust_data client_data;
	int result;
	int cselect;
	int tselect;
	int reconnect_flag;
	float dep_amount;
	float with_amount;
	char customer_account[8];
	char uname[10];
	char password[10];
	int running = 1;
	int validation_return;

	reconnect_flag=1; //Initiall set flag to 1 to open connection
	
	while (running)
	{
		while(strcmp(u_valid.isvalid,"V")!=0)
		{
		 	if(reconnect_flag==1)
			{
				//  Create a socket for the client
				client_socket = socket(AF_INET, SOCK_STREAM, 0);

				//  Name the socket as agreed with server	
				address.sin_family = AF_INET;
				address.sin_addr.s_addr = inet_addr("127.0.0.1");
				address.sin_port = 8484;
				len = sizeof(address);
		
				result = connect(client_socket, (struct sockaddr *)&address, len);
				reconnect_flag=0;
			}
			if (result == -1)
			{
				perror("CLIENT:CONNECTION ERROR");
				return 1;
			}
			
			system("clear");  //clear the screen

			cout<<"-= KNIGHT BANK ONLINE 1.0 =-\n"<<endl;
			
			cout<<"Username:";
			cin>>uname;
			strcpy(u_valid.uname,uname);
			cout<<"Password:";
			cin>>password;
			strcpy(u_valid.password,password);
			
			//send data through socket to server
			write(client_socket,(struct user_validation*)&u_valid, sizeof(u_valid));
			sleep(3);
			validation_return=read(client_socket, (struct user_validation*)&u_valid, sizeof(u_valid));
			
			if(strcmp(u_valid.isvalid,"I")==0)
			{
				cout<<"USER IS NOT VALID, PLEASE TRY AGAIN!"<<endl;
				sleep(3);
				close(client_socket);
				reconnect_flag=1;
			}

			cout<<"Validating user, please wait..."<<endl;
			
		}
		
		//cout<<u_valid.account_type<<endl;
		
		sleep(3);
		if(strcmp(u_valid.account_type,"C")==0)
		{
			system("clear");
			cout<<"-= KNIGHT BANK ONLINE 1.0 =-\n"<<endl;
			cout<<"Account #:";
			cout<<u_valid.account_number<<endl;
			cout<<"\nWelcome Customer!"<<endl;
			cout<<"1. Deposit Funds"<<endl;
			cout<<"2. Withdraw Funds"<<endl;
			cout<<"3. View Account"<<endl;
			cout<<"9. Quit"<<endl;		

			cout<<"\nSelect an option ->";
			cin>>cselect;

			switch(cselect)
			{

				case 1: 
					cout<<"Customer-Deposit Funds\n"<<endl;
					cout<<"Deposit Amount->";
					cin>>dep_amount;
					
					strcpy(client_data.bank_account_number,u_valid.account_number);
					client_data.bank_amount=dep_amount;
					client_data.bank_code=40;
				break;
				case 2: 
					cout<<"Customer-Withdraw Funds\n"<<endl;
					cout<<"Withdrawal Amount->";
					cin>>with_amount;
					
					strcpy(client_data.bank_account_number,u_valid.account_number);
					client_data.bank_amount=with_amount;
					client_data.bank_code=50;
				break;
				case 3: cout<<"Customer-View Account!"<<endl;
					client_data.bank_code=10;
					strcpy(client_data.bank_account_number,u_valid.account_number);
				break;
				case 9: 
						cout<<"Goodbye! Thank you for using Bank Knight Online!"<<endl;
						running=0;
						break;
				default:cout<<"Please select a number from the menu!"<<endl;
			}
		}
		else if(strcmp(u_valid.account_type,"T")==0)
		{
			system("clear");
			cout<<"-= KNIGHT BANK ONLINE 1.0 =-\n"<<endl;
			cout<<"Welcome Teller!"<<endl;
			cout<<"1. Deposit Funds for customer"<<endl;
			cout<<"2. Withdraw Funds for customer"<<endl;
			cout<<"3. View account of customer"<<endl;
			cout<<"4. Modify account of customer"<<endl;
			cout<<"5. Delete account of customer"<<endl;
			cout<<"6. Add new account"<<endl;
			cout<<"9. Quit"<<endl;
			
			cout<<"\nSelect an option ->";
			cin>>tselect;

			switch(tselect)
			{

				case 1: cout<<"Teller-Deposit Funds!"<<endl;
					cout<<"Teller-Deposit Funds\n"<<endl;
					cout<<"What is the account number ->"<<endl;
					cin>>customer_account;
					cout<<"\nDeposit Amount->";
					cin>>dep_amount;
				
					//Add values to struct
					client_data.bank_amount=dep_amount;
					strcpy(client_data.bank_account_number,customer_account);
					client_data.bank_code=40;
					break;
				case 2: 
					cout<<"Teller-Withdraw Funds"<<endl;
					cout<<"What is the account number ->"<<endl;
					cin>>customer_account;
					cout<<"\nWithdraw Amount->";
					cin>>with_amount;
				
					//Add values to struct
					client_data.bank_amount=with_amount;
					strcpy(client_data.bank_account_number,customer_account);
					client_data.bank_code=50;
					break;
				case 3: cout<<"Teller-View Account"<<endl;
					cout<<"What is the account number ->"<<endl;
					cin>>customer_account;
							
					//Add values to struct
					strcpy(client_data.bank_account_number,customer_account);
					client_data.bank_code=10;
				break;
				case 4: cout<<"Teller-Modify Account"<<endl;
					//WORK ON THIS OPERATION LATER!!!!!!!!!!!!!!
					cout<<"What is the account number ->"<<endl;
					cin>>customer_account;
					cout<<"\nWithdraw Amount->";
					cin>>with_amount;
				
					//Add values to struct
					client_data.bank_amount=with_amount;
					strcpy(client_data.bank_account_number,customer_account);
					client_data.bank_code=60;
				break;
				case 5: cout<<"Teller-Delete Account"<<endl;
					cout<<"What is the account number ->"<<endl;
					cin>>customer_account;
									
					//Add values to struct
					strcpy(client_data.bank_account_number,customer_account);
					client_data.bank_code=30;
				break;
				case 6: cout<<"Teller-Add New Account"<<endl;
					//WORK ON OPERATION LATER!!!!!!!!!!!!!!!!!!!!!!!!!
					cout<<"What is the account number ->"<<endl;
					cin>>customer_account;
					cout<<"\nWithdraw Amount->";
					cin>>with_amount;
				
					//Add values to struct
					client_data.bank_amount=with_amount;
					strcpy(client_data.bank_account_number,customer_account);
					client_data.bank_code=20;
				break;
				case 9: 
						cout<<"Goodbye! Thank you for using Bank Knight Online!"<<endl;
						running=0;
						break;
				default:cout<<"Please select a number from the menu!"<<endl;
			}	
		}
		else
		{
			cout<<"YOU ARE NEITHER!"<<endl;
		}
		
		write(client_socket,(struct bnb_cust_data*)&client_data, sizeof(client_data));
	
		cout<<"Please Wait..."<<endl;
		
		read(client_socket,(struct bnb_cust_data*)&client_data, sizeof(client_data));

		switch(client_data.bank_result_code)
			{
				case 0: cout<<"Operation executed successfully!"<<endl;
				break;
				case 11: cout<<"Bank account number not found!"<<endl;
				break;
				case 21: cout<<"Bank account must be 7 digits long!"<<endl;
				break;
				case 31: cout<<"Not enough funds to withdraw!"<<endl;
				break;
				case 51: 
						cout<<"Exceeds maximum amount allowed in an account! (500k max.)"<<endl;
				break;		
			}	

		/*if end command not entered, keep going
		if(running != 0)
		{
			//read from the socket
			readreturn = read(sockfd, buffer, BUFSIZ);
			valuereturn = read(sockfd, opcode, BUFSIZ);
			
			//set final array to null
			buffer[readreturn] = '\0';
			opcode[valuereturn] = '\0';
			
			//Display results to user
			cout << "Operator used: " << buffer << endl;
			cout << "Calculation returned is: " << opcode << endl;
			
		}*/
	}

	//close out the socket
	close(client_socket);
	return 0;

}

---

### Post by Mitch.Pitt on 2006-05-07
And now the server program... You will see where it will add values for a username password, etc.  They are supposed to be static.

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <string>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <iostream>

using namespace std;

struct user_validation
{
	char uname[10];
	char password[10];
	char account_number[8];
	char isvalid[2];
	char account_type[2]; //'C' for Customer, 'T' for Teller
};

int main()
{
	int server_socket, client_socket;
	socklen_t server_len, client_len;
	
	//  Network form of address structure
	struct sockaddr_in server_address;
	struct sockaddr_in client_address;
	struct user_validation u_valid;
	char account_names[3][10];
	char account_pass[3][10];
	char account_type[3][2];
	char account_number[3][8];
	
	int user_flag;
	int fork_result;
	int flags;
	char buffer[BUFSIZ];
	
	//Creation of socket
	server_socket = socket(AF_INET, SOCK_STREAM, 0);

	//using the AF_INET socket type
	server_address.sin_family = AF_INET;

	//using a loopback to test socket
	server_address.sin_addr.s_addr =
	inet_addr("127.0.0.1");

	//port 8888 will pass the values from server to client
	server_address.sin_port = 8484;

	//get the length of the server address
	server_len = sizeof(server_address);

	//Bind the socket
	bind(server_socket, (struct sockaddr*)&server_address, server_len);

	//listen on the socket
	listen(server_socket, 5);

	strcpy(account_names[0],"mitchpitt\0");
	strcpy(account_pass[0],"mitchpitt\0");
	strcpy(account_type[0],"C\0");
	strcpy(account_number[0],"1111112\0");
	strcpy(account_names[1],"joesmith\0");
	strcpy(account_pass[1],"jsmith1\0");
	strcpy(account_type[1],"C\0");
	strcpy(account_number[1],"2222223\0");
	strcpy(account_names[2],"bbrinkman\0");
	strcpy(account_pass[2],"teller1\0");
	strcpy(account_type[2],"T\0");

	while (1)
	{
		char ch;

		cout << "Server Waiting" << endl;

		//wait for a client to send values
		client_socket = accept(server_socket, (struct sockaddr *)&client_address, &client_len);

		cout<<"Ready to read"<<endl;
		read(client_socket, (struct user_validation*)&u_valid, sizeof(u_valid));

		cout<<u_valid.uname<<endl;
		cout<<u_valid.password<<endl;
		cout<<u_valid.isvalid<<endl;
		cout<<u_valid.account_type<<endl;

		cout<<"Account Names:";
		cout<<account_names[0]<<endl;
		cout<<"Enter Username:";
		cout<<u_valid.uname<<endl;
	
		if((strcmp(account_names[0],u_valid.uname)==0) && (strcmp(account_pass[0],u_valid.password)==0))
		{
			cout<<"USER IS CUSTOMER!"<<endl;
			strcpy(u_valid.isvalid,"V\0");
			strcpy(u_valid.account_type,account_type[0]);
			strcpy(u_valid.account_number,account_number[0]);
			user_flag=0;
		}
		else if((strcmp(account_names[1],u_valid.uname)==0) && (strcmp(account_pass[1],u_valid.password)==0))
		{
			cout<<"USER IS CUSTOMER!"<<endl;
			strcpy(u_valid.isvalid,"V\0");
			strcpy(u_valid.account_type,account_type[1]);
			strcpy(u_valid.account_number,account_number[1]);
			user_flag=1;
		}
		else if((strcmp(account_names[2],u_valid.uname)==0) && (strcmp(account_pass[2],u_valid.password)==0))
		{
			cout<<"USER IS TELLER!"<<endl;
			strcpy(u_valid.isvalid,"V\0");
			strcpy(u_valid.account_type,account_type[2]);
			user_flag=2;
		}
		else
		{
			cout<<"USER IS INVALID!"<<endl;
			strcpy(u_valid.isvalid,"I\0");
			//strcpy(u_valid.account_type,account_type[1]);
		}

		cout<<"Changed isvalid - ";
		cout<<u_valid.isvalid<<endl;	
		
		//send data through socket to server
		write(client_socket,(struct user_validation*)&u_valid, sizeof(u_valid));

		//*****************************************************************************	
		//Create a fork
		
		if((strcmp(u_valid.isvalid,"V")==0) && (strcmp(u_valid.account_type,"C")==0))
		{
				cout<<"FORKING CUSTOMER INTERFACE!"<<endl;
				fork_result = fork();
	    	{
					if (fork_result == -1)
					{
						cout << "Fork failed - exiting" << endl;
						return 1;
					}        

					if (fork_result == 0)		// We are the child - we'll exec reader
					{
						sprintf (buffer, "%d", client_socket);
						cout<<buffer<<endl;
						//start interface6 application
						execl ("customerint", "customerint", buffer,account_number[user_flag],(char *)0);
					}
				}//end fork
		}
		else if((strcmp(u_valid.isvalid,"V")==0) && (strcmp(u_valid.account_type,"T")==0))
		{
				cout<<"FORKING TELLER INTERFACE!"<<endl;
				fork_result = fork();
	    	{
					if (fork_result == -1)
					{
						cout << "Fork failed - exiting" << endl;
						return 1;
					}        

					if (fork_result == 0)		// We are the child - we'll exec reader
					{
						sprintf (buffer, "%d", client_socket);
						cout<<buffer<<endl;
						//start interface6 application
						execl ("tellerint", "tellerint", buffer,account_number[user_flag],(char *)0);
					}
				}//end fork
		}
	}  
	
	return 0;

}

---

### Post by LordHunter317 on 2006-05-07
Like I said, you have a bug.  You cannot read/write a struct the way you're doing it and expect it to work portably.  You must write it out member-by-member and read it the same way.   This is because the C and C++ standards allow for arbitrary padding of structs in any way the compiler sees fit.  Different versions of a compiler don't even do it in the same way.

Anyway, your applications has massive other issues to: your string handling is dangerous, virtually every string handling call you make is a potential buffer overflow, as written. 

You really shouldn't mix C and C++ strings and I/O.  Pick a method and use only that.  And you must check the length of input strings and truncate as necessary.

---

