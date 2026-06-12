---
title: "Implementing CRN Survey and A Simple Sequential MAC Protocol for CRN Learning"
date: 2012-07-01
forum: Programming Talk
---

### Post by Tetsh on 2012-07-01
Hello, I am trying make the modifications explained in a paper published by Mr.Usman Shahid & Mr.Tahir Maqsood for adding primary users for simulating cognitive radio networks using ns2.
The paper's name is : CRN Survey and A Simple Sequential MAC Protocol for CRN Learning

The PDF version for the paper can be downloaded here: [www.google.com/url?sa=t&rct=j&q=crn survey and a simple sequential mac protocol for crn learning&source=web&cd=3&ved=0CFAQFjAC&url=http%3A%2F%2Fwww.thinkmind.org%2Fdownload.php%3Farticleid%3Dcocora_2012_2_10_60013&ei=BoLwT93UJdP54QSLq-DHDQ&usg=AFQjCNHHBhK8SjSEapEfxw5Lq-ydYyAtiA&cad=rja]("http://www.google.com/url?sa=t&rct=j&q=crn%20survey%20and%20a%20simple%20sequential%20mac%20protocol%20for%20crn%20learning&source=web&cd=3&ved=0CFAQFjAC&url=http%3A%2F%2Fwww.thinkmind.org%2Fdownload.php%3Farticleid%3Dcocora_2012_2_10_60013&ei=BoLwT93UJdP54QSLq-DHDQ&usg=AFQjCNHHBhK8SjSEapEfxw5Lq-ydYyAtiA&cad=rja")
**_I have installed the CRCN patch for ns-2.31 and running it with no problems._**
Files needed to be modified are mobilenode.h, mobilenode.cc, phy.cc , packet.h , mac-simple.cc
I have some questions i hope someone can help me because i am running out of time for my graduation project.
The main idea is making node 4 & 5 as primary users and make them communicate over channel 2 forbidding communication of secondary users on this channel when in use with primary users.

[COLOR=Red][SIZE=3]_**A.Modifications in NS2 to Support Simple Sequential MAC for CRN**_[/SIZE][/COLOR]

First file: mobilenode.cc
Modification done: added the following two lines under MobileNode::MobileNode(Void)
```
   bind("isprimaryuser",&isprimaryuser);         //set wether the current node is a primary user or not
        bind("chanis",&chanis);                       //set channel for primary user
```Do I have to make an intialization for them as isprimaryuser=0; chanis=0; or not??

Second file: mobilenode.h
Modification done: added the following two lines under public 
```
int IsPrimaryUser() { return isprimaryuser;}
int ChanIs() { return chanis;}
```added the following under protected
```
  int isprimaryuser;
        int chanis;
```Third File: packet.h
Modifications done: added the following two lines under struct hdr_cmn
```
  int fromprimaryuser; //the field indicate whether it is a packet from primary user
        int fromCRuser; //the field indicate whether it is a packet from seconadry user
```Also added the following two lines under inline Packet* Packet::alloc()
```
   (HDR_CMN(p))->fromprimaryuser=0;
         (HDR_CMN(p))->fromCRuser=0;
```Fourth fle: phy.cc
Modification done: added the following line under 
[I]void
Phy::recv(Packet* p, Handler*)[/I] just after *struct hdr_cmn *hdr = HDR_CMN(p);*
```
if(node()->nodeid()==5 || node()->nodeid()== 4)
{
nchannel=2;
}

nchannel= hdr->channelindex_;
```[COLOR=black][COLOR=Red][SIZE=3]_**B. MAC Modifications**_[/SIZE][/COLOR][/COLOR]

Fifth file: mac-simple.cc
Modification done: Added the following codes under send function
[I]void
MacSimple::send(Packet *p, Handler *h)[/I] just after 
*hdr_cmn* ch = HDR_CMN(p);*
```

   if(((MobileNode*)(netif_->node())) -> IsPrimaryUser()==0)
{
   ch->fromCRuser=1;
   ch->fromprimaryuser=-1;
   ch->channelindex_=recvchan;
}
   else
{
   ch-> channelindex_=((MobileNode*)(netif_-> node()))->ChanIs();
   ch->fromCRuser=0;
   ch->fromprimaryuser= ch-> channelindex_;
}
```Also I have included the following at the beginning:
```
#include "mobilenode.h"
      #include "packet.h"
```Now recvchan to be used as a channel number in the MAC
Cognitive user sends channel number in channelindex_
whereas primary user sends its fixed channel number in
fromprimaryuser header field.

I have added the following code under the recv function *void MacSimple::recv(Packet *p, Handler *h)*  just after *struct hdr_cmn *hdr = HDR_CMN(p);*
```
        if (index_==4 || index_==5)
{
        chan=2;
        recvchan=chan;
}
int isprimaryuser = ((MobileNode*)(netif_-> node()))-> _IsPrimaryUser_;
if(isprimaryuser==1 && hdr->fromCRuser==1)
{
Packet::free(p);
return;
}
if(isprimaryuser==0 && hdr-> fromprimaryuser !=-1)
{
Totalchannels = ((MobileNode*)(netif_-> node()))-> number_of_channel;
recvchan++;
recvchan= recvchan % Totalchannels;
}
```Please note that the underlined part was written in the paper as IsPrimaryUser not IsPrimaryUser(). Should i add the brackets or not?

Sixth File: mac-simple.h
Modifications done: Added the following under *protected*
```
  int             recvchan;
        int             Totalchannels;

```When i try to compile ns2 again with make clean , make depend , make. I recieve this error:
```
mac/mac-simple.cc: In member function ‘virtual void MacSimple::recv(Packet*, Handler*)’:
mac/mac-simple.cc:132:9: error: ‘chan’ was not declared in this scope
mac/mac-simple.cc:133:9: error: ‘recvchan’ was not declared in this scope
mac/mac-simple.cc:135:56: error: argument of type ‘int (MobileNode::)()’ does not match ‘int’
mac/mac-simple.cc:143:1: error: ‘Totalchannels’ was not declared in this scope
mac/mac-simple.cc:144:1: error: ‘recvchan’ was not declared in this scope
mac/mac-simple.cc: In member function ‘void MacSimple::send(Packet*, Handler*)’:
mac/mac-simple.cc:234:22: error: ‘recvchan’ was not declared in this scope
make: *** [mac/mac-simple.o] Error 1

```Also here are the full modified files if someone needs them: [http://www25.zippyshare.com/v/98764626/file.html](http://www25.zippyshare.com/v/98764626/file.html)

And the original files from the CRCN patch: [http://www9.zippyshare.com/v/82060281/file.html](http://www9.zippyshare.com/v/82060281/file.html)

Any help will be greatly appreciated i hope i was clear enough.

---

