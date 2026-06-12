---
title: "Cannot read from stdin after initializing serial port"
date: 2011-02-05
forum: Programming Talk
---

### Post by ve4cib on 2011-02-05
I'm writing a program that will send & receive messages with a microcontroller board over a serial connection.  I'm using libserial to deal with the serial communication, but I'm running into a problem: as soon as I open the serial connection my program no longer prompts for input when I use cin>>{...}.  Rather than try to explain the behaviour in detail, I'll post the relevant code below, along with the buggy output.

**main.cpp**
```

#include <string.h>
#include <stdlib.h>
#include <SerialStream.h>
#include <iostream>
#include "main.h"

//(snipped)

int main(int argc, char** argv)
{
    using namespace std;
    
    const char* ttyDev = "/dev/ttyUSB0";
    
    // optionally override the default TTY device
    if(argc>1)
    {
        if(!strcmp(argv[1],"--help"))
        {
            printHelp();
            return 0;
        }
        else
        {
            ttyDev = argv[1];
        }
    }

    // initialize the serial port
    initSerialPort(ttyDev);
    if(!tty)
    {
        cout<<"Unable to open "<<ttyDev<<endl<<"Aborting."<<endl;
        return -1;
    }
    
    // loop through asking the user to select a port to query, until they send the quit command
    int cmd;
    unsigned char id;
    cmd = getUserInput();
    while(cmd != CMD_QUIT)
    {
        if(cmd==CMD_BROADCAST)
        {
            id = BROADCAST_ID;
        }
        else
        {
            id = (unsigned char)cmd;
        }
        
        if((id >= MIN_ID && id <= MAX_ID) || id==BROADCAST_ID)
        {
            // send the ID to the CM5 so we can query that servo
            tty->WriteByte(id);
        }
        else
        {
            cout<<"Invalid ID: IDs must be between "<<MIN_ID<<" and "<<MAX_ID<<" or ="<<CMD_BROADCAST<<endl;
            cout<<"Read: "<<cmd<<endl;
        }
                
        // get the next command
        cmd = getUserInput();
    }
    
    closeSerialPort();
    delete tty;
    cout<<"Goodbye"<<endl;
    return 0;
}


//(snipped)

// initialize the serial port, set the baud rate, etc...
void initSerialPort(const char* ttyDev)
{
    // open the serial port
    tty = new SerialPort::SerialPort(ttyDev);
    tty->Open();
    
    // set the baud rate to 57.6k
    tty->SetBaudRate(SerialPort::BAUD_57600);
    
    // set the frame to 8N1
    tty->SetCharSize(SerialPort::CHAR_SIZE_8);
    tty->SetParity(SerialPort::PARITY_NONE);
    tty->SetNumOfStopBits(SerialPort::STOP_BITS_1);
}

// close the serial port
void closeSerialPort()
{
    try
    {
        tty->Close();
    }
    catch(...)
    {
        // don't do anything
    }
}

// read a number from STDIN to determine what servo we're going to query
int getUserInput()
{
    using namespace std;
    
    int id;
    cout<<"Special Commands:"<<endl;
    cout<<"   -1: Quit"<<endl;
    cout<<"   255: Query all servos"<<endl;
    cout<<"Enter the ID of the servo to query: ";
    cin>>id;
    return id;
}

```


**Sample Output**
```

Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677
Special Commands:
   -1: Quit
   255: Query all servos
Enter the ID of the servo to query: Invalid ID: IDs must be between 0 and 20 or =255
Read: 32677

...

```


If I put getUserInput() *before* the call to initSerialPort the prompt works just fine.  It sits there and waits until I type in an integer.  But as soon as I initialize the serial port cin>>(integer) seems to magically read in a value from *somewhere* that isn't stdin.  My guess is that it's reading from the serial port or something, but I can't for the life of me figure out why.

To check if it was something overwriting the std namespace I tried using fgetc(stdin), and it had the same problem; it would read in a character from something, but not from the console.

This is my first time using libserial, so maybe I'm messing something up.  But if anyone has any suggestions for things to change/try please let me know.  I really appreciate the help.

---

