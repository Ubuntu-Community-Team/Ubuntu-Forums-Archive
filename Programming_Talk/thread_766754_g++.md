---
title: "g++"
date: 2008-04-25
forum: Programming Talk
---

### Post by fellya on 2008-04-25
hello,
I'm compiling my scripts using g++ -Wall -o my_file my_file.cc in sense simulator using g++ compiler and i'm getting this error:
/usr/lib/gcc/i686-pc-cygwin/3.4.4/../../../libcygwin.a(libcmain.o):(.text+0xab):undefined reference to '_WinMain@16'

can someone help me?
thank you.

---

### Post by Sockerdrickan on 2008-04-25
if you are using
int main() {

then change it to 
int main(int argc, char **argv) {

---

### Post by fellya on 2008-04-25
thank you for your answer,
 i'm not using c++ codes, it is a king of mix codes.
brief it is a tutorial that i'm trying to compile. check the codes below:

[PHP]#define queue_t HeapQueue

#include "../../common/sense.h"

#include "../../app/cbr.h"
#include "../../mob/immobile.h"
#include "../../net/flooding.h"
#include "../../net/aodvi.h"
#include "../../net/dsri.h"
#include "../../mac/null_mac.h"
#include "../../mac/mac_80211.h"
#include "../../phy/transceiver.h"
#include "../../phy/simple_channel.h"
#include "../../energy/battery.h"
#include "../../energy/power.h"
#include "../../util/fifo_ack.h"

#cxxdef net_component Flooding
#cxxdef net_struct Flooding_Struct

typedef CBR_Struct::packet_t app_packet_t;
typedef net_struct<app_packet_t>::packet_t net_packet_t;
typedef MAC80211_Struct<net_packet_t*>::packet_t mac_packet_t;

component SensorNode : public TypeII
{
public:

    CBR app;
    net_component <app_packet_t> net;
    MAC80211 <net_packet_t*> mac;
    // A transceiver that can transmit and receive at the same time (of course
    // a collision would occur in such cases)
    DuplexTransceiver < mac_packet_t > phy;
    // Linear battery
    SimpleBattery battery;
    // PowerManagers manage the battery
    PowerManager pm;
    // sensor nodes are immobile
    Immobile mob;
    // the queue used between network and mac
    FIFOACK3<net_packet_t*,ether_addr_t,unsigned int> queue;
    
    double MaxX, MaxY;  // coordinate boundaries
    ether_addr_t MyEtherAddr; // the ethernet address of this node
    int ID; // the identifier

    virtual ~SensorNode();
    void Start();
    void Stop();
    void Setup();
		outport void to_channel_packet(mac_packet_t* packet, double power, int id);
		inport void from_channel (mac_packet_t* packet, double power);
		outport void to_channel_pos(coordinate_t& pos, int id);
};

SensorNode::~SensorNode()
{
}

void SensorNode::Start()
{
}

void SensorNode::Stop()
{
}
void SensorNode::Setup()
{
    battery.InitialEnergy=1e6;
    app.MyEtherAddr=MyEtherAddr;
    app.FinishTime=StopTime()*0.9;
    app.DumpPackets=false;
    mob.InitX=Random(MaxX);
    mob.InitY=Random(MaxY);
    mob.ID=ID;
    net.MyEtherAddr=MyEtherAddr;
    net.ForwardDelay=0.1;
    net.DumpPackets=true;
    mac.MyEtherAddr=MyEtherAddr;
    mac.Promiscuity=true;
    mac.DumpPackets=true;
    pm.TXPower=1.6;
    pm.RXPower=1.2;
    pm.IdlePower=1.15;
    phy.TXPower=0.0280;
    phy.TXGain=1.0;
    phy.RXGain=1.0; 
    phy.Frequency=9.14e8;
    phy.RXThresh=3.652e-10;
    phy.CSThresh=1.559e-11;
    phy.ID=ID;

    connect app.to_transport, net.from_transport;
    connect net.to_transport, app.from_transport;
    
    connect net.to_mac, queue.in;
    connect queue.out, mac.from_network;
    connect mac.to_network_ack, queue.next;
    connect queue.ack, net.from_mac_ack;
    connect mac.to_network_data, net.from_mac_data ;
    
    //connect mac.to_network_data, net.from_mac_data ;
    //connect mac.to_network_ack, net.from_mac_ack;
    //connect net.to_mac, mac.from_network;
    
    connect mac.to_phy, phy.from_mac;
    connect phy.to_mac, mac.from_phy;

    connect phy.to_power_switch, pm.switch_state;
    connect pm.to_battery_query, battery.query_in;
    connect pm.to_battery_power, battery.power_in;

    connect phy.to_channel, to_channel_packet;
    connect mob.pos_out, to_channel_pos;
    connect from_channel, phy.from_channel;
}
component RoutingSim : public CostSimEng
{
public:
    void Start();
    void Stop();
    double MaxX, MaxY;
    int NumNodes;
    int NumSourceNodes;
    int NumConnections;
    int PacketSize;
    double Interval;
    SensorNode[]  nodes;
    SimpleChannel < mac_packet_t > channel;

    void Setup();
};

void RoutingSim :: Start()
{
}

void RoutingSim :: Stop()
{
    int i,sent,recv;
    double delay;
    for(sent=recv=i=0,delay=0.0;i<NumNodes;i++)
    {
			sent+=nodes[i].app.SentPackets;
			recv+=nodes[i].app.RecvPackets;
			delay+=nodes[i].app.TotalDelay;
    }
    printf("APP -- packets sent: %d, received: %d, success rate: %.3f, delay: %.3f\n",
		sent,recv,(double)recv/sent,delay/recv);
    for(sent=recv=i=0;i<NumNodes;i++)
    {
			sent+=nodes[i].net.SentPackets;
			recv+=nodes[i].net.RecvPackets;
    }
    printf("NET -- packets sent: %d, received: %d\n",sent,recv);
    for(sent=recv=i=0;i<NumNodes;i++)
    {
			sent+=nodes[i].mac.SentPackets;
			recv+=nodes[i].mac.RecvPackets;
    }
    printf("MAC -- packets sent: %d, received: %d\n",sent,recv);
}


void RoutingSim :: Setup()
{
    int i,j;
    nodes.SetSize(NumNodes);
    for(i=0;i<NumNodes;i++)
    {
			nodes[i].MaxX=MaxX;
			nodes[i].MaxY=MaxY;
			nodes[i].MyEtherAddr=i;
			nodes[i].ID=i;
	    nodes[i].Setup(); // don't forget to call this function for each sensor node
    }    

    channel.NumNodes=NumNodes;
    channel.DumpPackets=false;
    channel.CSThresh=nodes[0].phy.CSThresh;
    channel.RXThresh=nodes[0].phy.RXThresh;
    channel.PropagationModel=channel.FreeSpace;

    channel.Setup();

    for(i=0;i<NumNodes;i++)
    {
			connect nodes[i].to_channel_packet,channel.from_phy;
			connect nodes[i].to_channel_pos,channel.pos_in;
			connect channel.to_phy[i],nodes[i].from_channel ;
    }
    int src,dst;
    for(i=0;i<NumSourceNodes;i++)
    {
			for(j=0;j<NumConnections;j++)
			{
	    	do
	    	{
					src=Random(NumNodes);
					dst=Random(NumNodes);
	    	}while(src==dst); 
	    		nodes[src].app.Connections.push_back(
					make_triple(ether_addr_t(dst),Random(PacketSize)+PacketSize/2,
					Random(Interval)+Interval/2));
			}
    }
}[/PHP]

---

### Post by WW on 2008-04-25
fellya: Just a tip: enclosed your code in **[ code ]** and **[ /code ]** tags (but without the spaces around the word **code**).  The forum software will put the code in a box using a monospace font that preserves the indentation.  You can also try the **php** tag instead of **code**; this will use color, too.  You can use the EDIT button to edit a previous post; it would be helpful if you added the tags around the code that you listed above.

It looks like you are trying to use this software: [http://www.ita.cs.rpi.edu/sense/index.html](http://www.ita.cs.rpi.edu/sense/index.html)
You could try sending an email directly to the author(s) at RPI.

---

### Post by samjh on 2008-04-27
> **fellya said:**
> hello,
I'm compiling my scripts using g++ -Wall -o my_file my_file.cc in sense simulator using g++ compiler and i'm getting this error:
/usr/lib/gcc/i686-pc-cygwin/3.4.4/../../../libcygwin.a(libcmain.o):(.text+0xab):undefined reference to '_WinMain@16'

can someone help me?
thank you.

Looks like an issue with Cygwin.

I've noticed on the webpage of the author that there is separate source download for Windows.  I wonder if you're trying to compile the Windows source code in a Linux or Ubuntu environment.

If you're using Ubuntu, try downloading the non-Windows version: [http://www.ita.cs.rpi.edu/sense/download/sense-3.0.3.tar.gz](http://www.ita.cs.rpi.edu/sense/download/sense-3.0.3.tar.gz)

---

### Post by Zugzwang on 2008-04-28
> **fellya said:**
> thank you for your answer,
 i'm not using c++ codes, it is a king of mix codes.
brief it is a tutorial that i'm trying to compile. check the codes below:


I assume that you followed this tutorial: [http://www.ita.cs.rpi.edu/sense/sim_routing.cc.html]("http://www.ita.cs.rpi.edu/sense/sim_routing.cc.html")

However, you didn't paste the main() function from the bottom of the page into your code, so this is obviously missing!

---

