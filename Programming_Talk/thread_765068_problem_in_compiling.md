---
title: "problem in compiling"
date: 2008-04-24
forum: Programming Talk
---

### Post by fellya on 2008-04-24
hello,
I' m using gcc compiler to compile scripts combined with c++ codes. the scripts are one of the example in the tutorial about sense simulator.
to copile they've given two processes:
- cxx my_file.cc
-g++ -Wall -o my_file my_file.cxx

the first one is  giving this kind of error: error 0013 (../../energy/power.h,34):outport 'from_pm_node_up' of component 'pm' not connected.

I need someone expert in using sense simulator to help me.
thanks.


the scripts:
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
      //connect pm.from_pm_node_up;
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
}
int main(int argc, char* argv[])
{
    RoutingSim sim;

    sim.StopTime = 1000;
    sim.Seed = 1234;

    sim.MaxX = 2000;
    sim.MaxY = 2000;

    sim.NumNodes = 110;
    sim.NumConnections = 2;
    sim.PacketSize = 2000;
    sim.Interval = 100.0;
   
    if(argc >= 2) sim.StopTime = atof(argv[1]);
    if(argc >= 3) sim.NumNodes = atoi(argv[2]);
    sim.NumSourceNodes = sim.NumNodes / 10;
    if(argc >= 4) sim.MaxX = sim.MaxY = atof(argv[3]);
    if(argc >= 5) sim.NumSourceNodes = atoi(argv[4]);
    if(argc >= 6) sim.PacketSize = atoi(argv[5]);
    if(argc >= 7) sim.Interval = atof(argv[6]); 

    printf("StopTime: %.0f, Number of Nodes: %d, Terrain: %.0f by %.0f\n",
	   sim.StopTime, sim.NumNodes, sim.MaxX, sim.MaxY);
    printf("Number of Sources: %d, Packet Size: %d, Interval: %f\n",
	   sim.NumSourceNodes, sim.PacketSize, sim.Interval);

    sim.Setup();
    sim.Run();

    return 0;
}[/PHP]

---

