---
title: "Overlapped and Non-overlapped Serial Programming"
date: 2007-05-30
forum: Programming Talk
---

### Post by budge1984 on 2007-05-30
Hello,

I'm trying to code a program that accepts data on a virtual com port and then forwards it through the physical com port to an external device. The external device then sends data back to the physical port which my program directs to the virtual port. The virtual port is "connected" to a third party program.

Now, my question is: Is it necessary to use overlapped operation if at no point operations actually overlap? You see, at no stage does my program need to perform operations simultaneously. It simply is a "go-between" between two external parties. It receives and sends in one direction and then receives and sends back the other direction.

I have coded this program using non-overlapped operation and WaitCommEvent(). It hangs the second time it calls WaitCommEvent to receive data from the external device. I would assume that because we are dealing with two separate com ports then the WaitCommEvent calls would not interfere with each other. What am i not understanding? 

Thanking you in advance.

budge.

```


#include <windows.h>
#include <iostream>
#include <string>
using namespace std;
using std::string;


HANDLE hSerial3 = CreateFile("COM3",
					GENERIC_READ | GENERIC_WRITE,
					0,
					0,
					OPEN_EXISTING,
					FILE_ATTRIBUTE_NORMAL,
					0);
					
HANDLE hSerial1 = CreateFile("COM1",
					GENERIC_READ | GENERIC_WRITE,
					0,
					0,
					OPEN_EXISTING,
					FILE_ATTRIBUTE_NORMAL,
					0);

void sendbackOK( ) {
			
			char writeBuff[50 + 1] = {0};
			DWORD dwBytesWrite = 0;	
			
			// Write response to outgoing buffer
			sprintf(writeBuff,"OK");
			
			if(!WriteFile(hSerial3, writeBuff, 50, &dwBytesWrite, NULL)){
				// error occured. Report to User.
				cout << "ERROR OCCURED IN WRITING TO SERIAL PORT" << "\n";
			}
			else
				cout << "SENT RESPONSE: " << writeBuff << "\n";
					
}

void sendbackCONNECT( ) {
			
			char writeBuff[50 + 1] = {0};
			DWORD dwBytesWrite = 0;	
			
			// Write response to outgoing buffer
			sprintf(writeBuff,"CONNECT 9600");
			
			if(!WriteFile(hSerial3, writeBuff, 50, &dwBytesWrite, NULL)){
				// error occured. Report to User.
				cout << "ERROR OCCURED IN WRITING TO SERIAL PORT" << "\n";
			}
			else
				cout << "SENT RESPONSE: " << writeBuff << "\n";
					
}


void forwardtoCOM1(char data[]) {
			
			char writeExtBuff[64+1] = {0};
			DWORD dwBytesWrite = 0;	
			
			// Write response to outgoing buffer
			sprintf(writeExtBuff,data);
			
			if(!WriteFile(hSerial1, writeExtBuff, 64, &dwBytesWrite, NULL)){
				// error occured. Report to User.
				cout << "ERROR OCCURED IN WRITING TO SERIAL PORT" << "\n";
			}
			else
				cout << "SENDING DATA: " << writeExtBuff << "\n";
}

void forwardtoCOM2(char data[]) {
			
			char writeExtBuff[64+1] = {0};
			DWORD dwBytesWrite = 0;	
			
			// Write response to outgoing buffer
			sprintf(writeExtBuff,data);
			
			if(!WriteFile(hSerial3, writeExtBuff, 64, &dwBytesWrite, NULL)){
				// error occured. Report to User.
				cout << "ERROR OCCURED IN WRITING TO SERIAL PORT" << "\n";
			}
			else
				cout << "SENDING DATA: " << writeExtBuff << "\n";
}

void getResponse()  {
	
	DWORD dwCommEvent;
	DWORD dwBytesRead;
	char readBuff;
	char receivedstring[32];
	string s;
	int i = 0;
	
	// Check that serial port can be opened:
	if(hSerial1==INVALID_HANDLE_VALUE){
		if(GetLastError()==ERROR_FILE_NOT_FOUND){
			// serial port does not exist. Inform User.
		}
		// some other error has occured. Inform User.
	}
	
	// Define Parameters for serial port:
	DCB dcbSerialParams = {0};
	dcbSerialParams.DCBlength=sizeof(dcbSerialParams);
	
	if (!GetCommState(hSerial1, &dcbSerialParams)) {
		// error getting state
	}
	
	dcbSerialParams.BaudRate=CBR_9600;
	dcbSerialParams.ByteSize=8;
	dcbSerialParams.StopBits=ONESTOPBIT;
	dcbSerialParams.Parity=NOPARITY;
	
	if(!SetCommState(hSerial1, &dcbSerialParams)){
		// error setting serial port state
	}
	
	// Set a timeout:
	COMMTIMEOUTS timeouts;
	timeouts.ReadIntervalTimeout=1;  // Specify time-out between charactor for receiving
	timeouts.ReadTotalTimeoutConstant=1; // Specify value is added to the product of the ReadTotalTimeoutMultiplier member
	timeouts.ReadTotalTimeoutMultiplier=1; // Specify value that is multiplied by the requested number of bytes to be read. 
	timeouts.WriteTotalTimeoutConstant=100;
	timeouts.WriteTotalTimeoutMultiplier=10;
	
	if(!SetCommTimeouts(hSerial1, &timeouts)){
		cout << "ERROR SETTTING TIMEOUTS"  << endl;
		// error occures setting timeouts. Inform User.
	}
	
	if (!SetCommMask(hSerial1, EV_RXCHAR)) {
	   cout << "ERROR: Error setting EV_RXCHAR mask!." << "\n";
	   // Error setting communications event mask
	}
	
	   	if (dwCommEvent.WaitCommEvent(hSerial1, &dwCommEvent, NULL)) {
	     
	    	do {
	        	if (ReadFile(hSerial1, &readBuff, 1, &dwBytesRead, NULL)) {
	            	// A byte has been read; process it.
					receivedstring[i] = readBuff;
					i++;
	        	}
		        else {
		           // An error occurred in the ReadFile call.
		           cout << "ERROR IN READFILE CALL" << endl;
		           
		        }
		        break;
		           
	      	} while (dwBytesRead);
	   		// Convert array to String
		   	forwardtoCOM2(receivedstring);
		   	s = receivedstring;
		   	
		   	// Print what was received to standard out
		   	cout << ("RECEIVED STRING AND SENT: ") << s << endl; 
	
		   	for (int j = 0; j<32; j++) {
				receivedstring[j] = NULL;
			}
			
		   	i=0;	
		
		}	
		
		else {
		    // Error in WaitCommEvent
			
		}
	
	
}


int main() {					
	
	cout << "Starting Program..." << endl;
	
	// Check that serial port can be opened:
	if(hSerial3==INVALID_HANDLE_VALUE){
		if(GetLastError()==ERROR_FILE_NOT_FOUND){
			// serial port does not exist. Inform User.
		}
		// some other error has occured. Inform User.
	}
	
	// Define Parameters for serial port:
	DCB dcbSerialParams = {0};
	dcbSerialParams.DCBlength=sizeof(dcbSerialParams);
	
	if (!GetCommState(hSerial3, &dcbSerialParams)) {
		// error getting state
	}
	
	dcbSerialParams.BaudRate=CBR_9600;
	dcbSerialParams.ByteSize=8;
	dcbSerialParams.StopBits=ONESTOPBIT;
	dcbSerialParams.Parity=NOPARITY;
	
	if(!SetCommState(hSerial3, &dcbSerialParams)){
		// error setting serial port state
	}
	
	// Set a timeout:
	COMMTIMEOUTS timeouts={0};
	timeouts.ReadIntervalTimeout=20;
	timeouts.ReadTotalTimeoutConstant=100;
	timeouts.ReadTotalTimeoutMultiplier=10;
	timeouts.WriteTotalTimeoutConstant=50;
	timeouts.WriteTotalTimeoutMultiplier=10;
	
	if(!SetCommTimeouts(hSerial3, &timeouts)){
		// error occures setting timeouts. Inform User.
	}
	
	
	////////////////////////////////////////////////////////////////////
	//		READ RECEIVED COMMANDS FROM MV90 AND DEAL WITH THEM APPROPRIATELY
	////////////////////////////////////////////////////////////////////
	
	DWORD dwCommEvent;
	DWORD dwBytesRead;
	char readBuff;
	char receivedstring[64];
	
	string s;

	
	int i = 0;
	
	if (!SetCommMask(hSerial3, EV_RXCHAR))
	   cout << "ERROR: Error setting EV_RXCHAR mask." << "\n";
	   // Error setting communications event mask
	
	while (true) {
	   	if (WaitCommEvent(hSerial3, &dwCommEvent, NULL)) {
	      	
	    	do {
	        	if (ReadFile(hSerial3, &readBuff, 1, &dwBytesRead, NULL)) {
	            	// A byte has been read; process it.
					receivedstring[i] = readBuff;
					i++;
	        	}
		        else
		           // An error occurred in the ReadFile call.
		           break;
		           
	      	} while (dwBytesRead);
	   		// Convert array to String
		   	s = receivedstring;
		   	
		   	// Print what was received to standard out
		   	cout << ("RECEIVED: ") << s << "\n";; 
	   		
			
			if (s.substr(0,4) == "ATE0")  {
				sendbackOK();
			
			}
			
			else if (s.substr(0,4) == "ATH0")  {
				sendbackOK();
			}
			
			else if (s.substr(0,5) == "AT&D2")  {
				sendbackOK();
			}
			
			else if (s.substr(0,20) == "ATS7=60DTZIGBEENODE1") {
				sendbackCONNECT();
			}
			
			else {
				//SINCE CONNECTION MADE: FORWARD DATA TO COM1
				forwardtoCOM1(receivedstring);
				getResponse();
				
				
			}
			
			for (int k = 0; k<64; k++) {
				receivedstring[k] = NULL;
			}
			
		   	i=0;
		   	
		}	
		
		else
		    // Error in WaitCommEvent
		   	break;
	   	
	}
}


```

---

