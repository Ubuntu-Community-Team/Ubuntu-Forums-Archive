---
title: "Stack Overflow"
date: 2010-02-08
forum: Programming Talk
---

### Post by primenu on 2010-02-08
Hi, I am trying to simulate the wormwhole routing network topology in c++.
I am using a trace file to read the feed the packets to the network, the trace file contains, source, destination, and the message size. So depending upon the message size, it is divided into packets. In my trace file messages would either be of size 8 , 16, 14000 unit(assuming network has the capacity to transfer 8 units in one cycle), I divide the packet into chunks of size unit 8.The movement in the network would thus be in wormlike fashion as to the property of wormwhole routing.
Whenever the the packet flits start arriving at the destination, which I think I am immediately freeing the memory assigned to that flit.The problem is when the number of messages fed into the network is below 1000, my program works fine, but with the increase in number of message it crashes. 
I used valgrind to track the errors, which to my disappointment I am not so good at using it, being a learner, and also gdb.
Here is the error I get using Valgrind:

==22905== Stack overflow in thread 1: can't grow stack to 0xBDE89FE8
==22905== 
==22905== Process terminating with default action of signal 11 (SIGSEGV)
==22905== Access not within mapped region at address 0xBDE89FE8
==22905== at 0x4211DA81: _IO_file_xsputn@@GLIBC_2.1 (in /lib/libc-2.5.so)
==22905== Stack overflow in thread 1: can't grow stack to 0xBDE89FE4
==22905== 
==22905== Process terminating with default action of signal 11 (SIGSEGV)
==22905== Access not within mapped region at address 0xBDE89FE4
==22905== at 0x40011D0: _vgnU_freeres (vg_preloaded.c:56)
==22905== 
==22905== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 16 from 1)
==22905== malloc/free: in use at exit: 17,945 bytes in 756 blocks.
==22905== malloc/free: 4,062,252 allocs, 4,061,496 frees, 59,790,198 bytes allocated.
==22905== For counts of detected errors, rerun with: -v
==22905== searching for pointers to 756 not-freed blocks.
==22905== checked 6,656,512 bytes.
==22905== 
==22905== LEAK SUMMARY:
==22905== definitely lost: 333 bytes in 18 blocks.
==22905== possibly lost: 1,108 bytes in 56 blocks.
==22905== still reachable: 16,504 bytes in 682 blocks.
==22905== suppressed: 0 bytes in 0 blocks.
==22905== Use --leak-check=full to see details of leaked memory.
Segmentation fault

And the error while using gdb:

Program received signal SIGSEGV, Segmentation fault.
0x4211da81 in _IO_new_file_xsputn () from /lib/libc.so.6
(gdb) bt full
#0 0x4211da81 in _IO_new_file_xsputn () from /lib/libc.so.6
No symbol table info available.
#1 0x4211412f in fwrite () from /lib/libc.so.6
No symbol table info available.
#2 0x001f8706 in ?? () from /usr/lib/libstdc++.so.6
No symbol table info available.
#3 0x001f43db in std::num_put<char, std:streambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long> () from /usr/lib/libstdc++.so.6
No symbol table info available.
#4 0x001f4650 in std::num_put<char, std:streambuf_iterator<char, std::char_traits<char> > >::do_put () from /usr/lib/libstdc++.so.6
No symbol table info available.
#5 0x001fcf0d in std:stream:perator<< () from /usr/lib/libstdc++.so.6
No symbol table info available.
#6 0x0804cff3 in node::update_node (this=0x911c440) at node.cc:158
temp = (._79 *) 0x911f004
flit = (flit_pkt *) 0x911f004
#7 0x0804d5a9 in node::sim_update (this=0x911c440) at node.cc:295
No locals.
If I am running into unending rucursion, my program runs fine with fewer messages like when there are 1000 messages in total sent to the mesh.
Below is the code for the "node" where the packet is divided into flits and then sent for the destination. 
```
#include "node.h"
#include <iostream>
#include <cstdlib>

using namespace std;

node::node(int x,int y){
	Xpos = x;
	Ypos = y;
	Msg_Sent = 0;
	Msg_Received = 0;
	Msg_Reconsiled = 0;
	fragmented = true;
	packt_number = 0;
	msg_size = 0;
	Input_Channel = new IVC();
	Output_Channel = new IVC();
	Input_Channel->Status = -1;
	Output_Channel->Status = -1;
}

void node::initiate_ports(switches *switch_t){

	this->node_to_switch = new node_to_switch_port(switch_t);
}
void node::fragmentation(void){

		int i = packt_number;
		while(i < (msg_size / flitSize )){
			Bodyflit = new flit_pkt();
			Bodyflit->type = 0;
			if(i == 1){
				Bodyflit->next = Headflit->next;
				Headflit->next = Bodyflit;
				Previousflit = Bodyflit;
			}else{
				
				Bodyflit->next = Previousflit->next;
				Previousflit->next = Bodyflit;
				Previousflit = Bodyflit;
			}
			buffer_queue.push_back(Bodyflit);
			i++;
			if (buffer_queue.size() >= 100){ //This numbeer doesn't hold any significant meaning, In case the msg_size is big so not to create huge number of flits..
				packt_number = i;
				return;
			}
		}
		buffer_queue.push_back(Tailflit);
		fragmented = true;
		packt_number = 0;
}


void node::update_node(double time_stamp, string msg_type, int Dest_Node, int msg_size){

	int xpos,ypos;
	msg_pkt *packets;
	packets = new msg_pkt();
	packets->Destination = Dest_Node;
	packets->msg_size = msg_size;
	packets->msg_type = msg_type;
	packets->time_stamp = time_stamp;
	msg_waiting_queue.push_back(packets);
	update_node();
}

void node::compare_message(msg_pkt *pkt){

	msg_waiting_queue.remove(pkt);
	delete pkt;
	Msg_Reconsiled++;

/*	This portion of code needs revision, so whenever the message of type recv is received from the simulator, it is immediately removed from the msg_waiting_queue. It is very inefficient, because I should be ignoring it immediately upon receive instead of outing it in a queue, but any help in finding error would be appreciated
for (list<msg_pkt*>::iterator it=receipt_list.begin(); it!=receipt_list.end(); ++it){
				msg_pkt *temp =  *it;
			if(pkt->msg_size == temp->msg_size && pkt->Destination == temp->Destination){
				cout<<"\n Message Received at Node:["<<Xpos<<"]["<<Ypos<<"]";
				msg_waiting_queue.remove(pkt);
				receipt_list.remove(temp);
				delete pkt;
				delete temp;
				Msg_Reconsiled++;
				return;
			}
		}
/*
}
//This function, does the fragmentation of the packets in flits of size 8 units here.
void node::update_node(){

	flit_pkt *flit;
	if(msg_waiting_queue.size() > 0){
		msg_pkt *temp = msg_waiting_queue.front();
		if (temp->msg_type == "recv"){
			compare_message(temp);
			return;
		}else if(temp->msg_type == "send"){
			if(buffer_queue.empty() && Output_Channel->Status == -1){
				int xpos,ypos;
				msg_waiting_queue.pop_front();
				xpos=temp->Destination / (row);
				ypos=temp->Destination % (column);
				this->msg_size = temp->msg_size;
				Msg_Sent++;
				Headflit = new flit_pkt();
				Tailflit = new flit_pkt();
				Headflit->next = Tailflit;
				Headflit->type = 1;
				Headflit->source[0] = Xpos;
				Headflit->destin[0] = xpos;
				Headflit->source[1] = Ypos;
				Headflit->destin[1] = ypos;
				Headflit->time_stamp = temp->time_stamp;
				Headflit->msg_size =   temp->msg_size;
				Tailflit->type = -1;
				Tailflit->next = NULL;
				buffer_queue.push_back(Headflit);
				packt_number = 1;
				fragmented = false;
				fragmentation();		
				delete temp;	
			}
		}
	}
	if(!fragmented){
		fragmentation();
	}
		
	while(! buffer_queue.empty()){

	flit = buffer_queue.front();	
		if(flit->type == 1 && Output_Channel->Status == -1){	
			// for Head Flit the Ideal Channel is to be selected
			Output_Channel->Status = 1;							// Change to Active, Message Waiting to be sent to the switch
			Output_Channel->flit_buffer.push_back(flit);
			// //cout<<"\n Header Filt pkt pushed to output channel:";			
			buffer_queue.pop_front();
			// push the flit into flitbuffer of the VC
	
		}else if(flit->type == 0 && Output_Channel->Status == 1 && Output_Channel->flit_buffer.size() < flit_size){
			// for body flit Check if the Status is Active and buffer not full
			Output_Channel->flit_buffer.push_back(flit);		// push the flit into flitbuffer of the VC
			buffer_queue.pop_front();
			
		}else if(flit->type == -1 && Output_Channel->Status == 1 && Output_Channel->flit_buffer.size() < flit_size){
			Output_Channel->flit_buffer.push_back(flit);
			buffer_queue.pop_front();
		}else{
			break;
		}
	}
	if(Input_Channel->Status != -1){
		while(!Input_Channel->flit_buffer.empty()){
			if(Input_Channel->flit_buffer.front()->type == -1){
				received_queue.push_back(Input_Channel->flit_buffer.front());
				flit = Input_Channel->flit_buffer.front();
				Input_Channel->flit_buffer.pop_front();							
				Input_Channel->Status = -1;
				pkt_Received();

			}else if(Input_Channel->flit_buffer.front()->type == 1 || Input_Channel->flit_buffer.front()->type == 0){
				received_queue.push_back(Input_Channel->flit_buffer.front());			
				flit = Input_Channel->flit_buffer.front();
				Input_Channel->flit_buffer.pop_front();
				pkt_Received();
			}
		}

	}
}
//This function could be called only after the whole worm is received at the node, but if the messages are of very big size, the packets could be taking a lot of memeory so I modified it to delete the all the packets received except the last received to keep track that the worm is intact
void node::pkt_Received(){

	if(!received_queue.empty()){
		current = received_queue.front();
		received_queue.pop_front();
		if(current->type == 1){
			previous = current;
			msg_pkt *packet = new msg_pkt();
			packet->time_stamp = current->time_stamp;
			packet->msg_size   = current->msg_size;
			packet->Destination = current->source[0]*row + current->source[1]; 
			receipt_list.push_back(packet);
			delete packet;
			pkt_Received();
		}else 
			if(previous->next != current){
				cout<<"\nError While Receiving Pkt Data at Node :["<<Xpos<<"]["<<Ypos<<"]";
				exit(0);
			}else if(current->type == -1){
//				cout<<"\n Tail of packet received:";
				delete current;
				delete previous;
				current = NULL;
				previous = NULL;
				Msg_Received++;
				return;
			}else{
				delete previous;
				previous = current;
				pkt_Received();	
			}
		}
}
//Transfers the flits stored in the outgoing buffer to the corresponding home switch, thrugh node_to_switch_port, which is object of fren class node_to_switch_port for class switches, thus it can inject the packets into the Input_Channel of the respective switch

void node::eject_message(void){

	if(Output_Channel->flit_buffer.size() > 0 && Output_Channel->Status != -1){
		flit_pkt *flit = Output_Channel->flit_buffer.front();
		if(flit->type == 1 && node_to_switch->eject_message(flit)){	// for Head Flit the Idle Channel is to be selected
			Output_Channel->Status = 1;				// Change to Active
			Output_Channel->flit_buffer.pop_front();// Empty the flit stored in the Buffer of OutChannel
		}else if(flit->type == 0 && node_to_switch->eject_message(flit) ){
			Output_Channel->flit_buffer.pop_front();
		}else if(flit->type == -1 &&  node_to_switch->eject_message(flit) ){
			Output_Channel->Status = -1;		//Change the Channel Status as Idle
			Output_Channel->flit_buffer.pop_front();
		}
	}	
}
//These functions are called when thhere are no messages coming from the simulator, thus to send all the waiting messages before stopping the simulation
bool node::sim_update(){
	update_node();
	if(Input_Channel->Status != -1 && !msg_waiting_queue.empty() ){
		return false;
	}
	else
		return true;
}
//These functions are called when thhere are no messages coming from the simulator, thus to send all the waiting messages before stopping the simulation

bool node::sim_communicate(){
	eject_message();
	if(Output_Channel->Status != -1 && !msg_waiting_queue.empty() ) { 
		return false;
	}
	else
		return true;
}


int node::print_result(int *Msg_Rec){
	cout<<"\n["<<Xpos<<"]["<<Ypos<<"] Msg_Received:"<<Msg_Received<<", Msg_Sent: "<<Msg_Sent<<", MsgReconsile: "<<Msg_Reconsiled;
	*Msg_Rec = Msg_Received;
	return Msg_Sent;
}

void node::clear_memory(){
	delete Input_Channel;
	delete Output_Channel;
	delete node_to_switch;
}
```
This is only for the node..other classes are switches, swich_port, switch_to_node_port, node_to_switch_port and simulate.
simulate calls the function update and communicate for all the switches and nodes in the mesh. Also sends the message to the corresponding source node reading the trace file. The classes switches and nodes communicate to each other using objects of class *_port..Any help or suggestion would be highly appreciated

---

### Post by dwhitney67 on 2010-02-08
It's amazing the you can keep track of that code; indentation and spacing are not the best.

I found this issue; it may or not be what is causing your segmentation violation:
```

void node::compare_message(msg_pkt *pkt){

	msg_waiting_queue.remove(pkt);
	delete pkt;
	Msg_Reconsiled++;

/*	This portion of code needs revision, so whenever the message of type recv is received from the simulator, it is immediately removed from the msg_waiting_queue. It is very inefficient, because I should be ignoring it immediately upon receive instead of outing it in a queue, but any help in finding error would be appreciated
for (list<msg_pkt*>::iterator it=receipt_list.begin(); it!=receipt_list.end(); ++it){
				msg_pkt *temp =  *it;
			if(pkt->msg_size == temp->msg_size && pkt->Destination == temp->Destination){

```

At the beginning of the method, you destroyed the 'pkt' object with the call to delete.  Then you try to access the same 'pkt' within the if-statement conditional.  Boom!


P.S.  compare_message() is being called from update_node().

---

### Post by primenu on 2010-02-08
For now, I have commented the whole portion in the compare_message() which I have to deal with later. I just delete the *pkt for now, But even with this problem is not solved. What I couldn't understand, why the program runs while the relatively fewer messages , with the increase in number of message put into the mesh it crashes..

---

### Post by dwhitney67 on 2010-02-08
Your program is crashing due a segmentation violation (SIGSEGV).  It possibly means that you are attempting to write, or read, from an invalid address.

Run your program in the debugger, to see exactly where it crashes.  Then examine the variables within the general area to see which are 'unreasonable'.

Pay good attention when popping from your 'queues' (are they deques?).  You do not want to over-pop your queues, for this could lead to a segmentation violation.  This little program below demonstrates this:
```

#include <deque>

int main()
{
   std::deque<int*> mydeck;

   mydeck.push_front(new int(10));
   mydeck.push_front(new int(20));
   mydeck.push_front(new int(30));

   int* val1 = mydeck.front(); mydeck.pop_front();
   int* val2 = mydeck.front(); mydeck.pop_front();
   int* val3 = mydeck.front(); mydeck.pop_front();

   delete val1;
   delete val2;
   delete val3;

   mydeck.front(); mydeck.pop_front();
}

```

---

### Post by primenu on 2010-02-08
thanks for the suggestion. I am trying to figure the reason and the place of the segmentation fault in the code.
I using  a priority queue to store values, which is regularly popped and pushed. 
What causes the error: 
(gdb) print my_queue.size()
Cannot access memory at address 0xbf5ffffc,
Gdb gives: Program received signal SIGSEGV, Segmentation fault error at this point
At this point of the code, I am trying to push the value into the my_queue.

---

### Post by Zugzwang on 2010-02-08
@OP: Is is possible that in the rest of your code, you allocate an arrays whose size is determined at runtime? Example: "Bigstruct package_data[nof_packages]"? 

Then you might spend most of the stack space on these arrays. Then, overflows in further function calls can occur even without recursion. Try to process a *much* higher number of packages and see where the program crashes. If that doesn't help, see if you find any of these array-allocations on the stack.

---

### Post by Maz_ on 2010-02-08
i'd suggest allocating large data structures from heap, and to avoid maintaining unnecessary information.

---

