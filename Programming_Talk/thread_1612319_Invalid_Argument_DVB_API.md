---
title: "Invalid Argument DVB API"
date: 2010-11-03
forum: Programming Talk
---

### Post by Dave.YNA on 2010-11-03
Hey everyone. I'm pretty new to all this programming stuff and in fact have only started to make some software that I can't seem to find the equivalent of so please forgive my ignorance if I have missed anything. Also considering the error I am getting, I am hoping that I am just making a newbie syntax or programming error and that the general programmer may be able to point out my stupidity.   

As for a little background:I am trying to make a signal meter. Like one an installer would use to peak at SAT strength. All the current apps out there fail at this because they all try to demux the stream so you need a full set of parameters for peeking at any satellite also encryption means that some sats are inaccessible for peeking. 

Anyway enough babble. I have managed to squirm through enough tutorials and trailing with many errors to get my code to the following state...

The problem I am getting is that I cannot seem to set the frontends frquency and symbol rate using FE_SET_FRONTEND () in the DVB API. It returns an error of

FE_SET_FRONTEND failed: Invalid argument

As far as I can see, my arguments look the same as the examples I have found on the internet.   

My code looks like this

```
#include <QtCore/QCoreApplication>
#include <iostream>
#include <string>
#include <sys/ioctl.h>
#include <stdio.h>
#include <stdint.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

#include <linux/dvb/dmx.h>
#include <linux/dvb/frontend.h>
#include <sys/poll.h>

#define DMX "/dev/dvb/adapter0/demux0"
#define FRONT "/dev/dvb/adapter0/frontend0"

int front, ans; //Front is important for giving address of frontend (i think in number form)
std::string quit; // Nothing important
fe_status_t status; //Important for looking at Frontend Status



struct dvb_frontend_info info; //Very important for FE info. Creates a new struct that you can add all the stats to
struct dvb_frontend_parameters frontend;
struct dvb_qpsk_parameters qpsk;

fe_delivery_system_t system = SYS_DVBS2;
uint32_t frequency = 11727;
fe_modulation_t modulation = PSK_8;
uint32_t symbol = 25000;
fe_code_rate_t  fec = FEC_AUTO;
uint32_t signal;



int main(int argc, char *argv[])
{

    QCoreApplication a(argc, argv);


    if((front = open(FRONT,O_RDWR)) < 0)
    {
        perror ("FRONTEND DEVICE: ");
        return -1;
            }
    else
        std::cout << "FE Started\r"; //GET THE INFO HERE....NEED TO MAKE A NEW STRUCT ABOVE FOR IT TO WORK
    ioctl (front, FE_GET_INFO, &info);
    std::cout << info.name;

    frontend.frequency = frequency;
    frontend.u.qpsk.symbol_rate = symbol;
    frontend.u.qpsk.fec_inner = fec;

    ioctl (front, FE_GET_FRONTEND, &frontend);
    std::cout << "\r" << frontend.frequency;
    std::cout << "\r" << frontend.u.qpsk.symbol_rate;

    if (ioctl(front, FE_SET_FRONTEND,&frontend) < 0) {
       perror("ioctl FE_SET_FRONTEND failed");
       close(front);
       return -1;
     }




    ioctl(front,FE_READ_SIGNAL_STRENGTH, &signal);
            std::cout << "\r" << signal << "\r";


    //STATUS's
    ioctl (front, FE_READ_STATUS, &status);
    if (status & FE_HAS_LOCK)
        fprintf(stderr, "FE_HAS_LOCK\n");
      else
        fprintf(stderr, "no lock...\n");
    if (status & FE_HAS_SIGNAL)
          fprintf(stderr, "FE_HAS_SIGNAL\n");
        else
          fprintf(stderr, "no Signal...\n");



    return a.exec();
}

// std::cout << “My first C++ program. \n”;

// return 0;

```

Any help people can give me would be great...After spending two days stumped I think it is time to seek the help of those wiser than myself :)

Thanks in advance!

---

