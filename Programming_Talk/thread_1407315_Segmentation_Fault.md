---
title: "Segmentation Fault"
date: 2010-02-15
forum: Programming Talk
---

### Post by primenu on 2010-02-15
I am using list in C++ for my program to store and messages , the messages are structure pointers.I am getting segmentation fault:

Program received signal SIGSEGV, Segmentation fault.
0x0804c5bc in switch_port::eject_message (this=0x80571a8, 
    flit=0x805a878, VChannel=4, N1=1, N2=2, InputVC=5)
    at switch_port.cc:53
53        }else if(flit->type == 0 && owner->Input_Channel[VChannel]->Status == 1 && owner->Input_Channel[VChannel]->flit_buffer.size() < flit_size && owner->Input_Channel[VChannel]->InputVC == InputVC){

here, the Input_Channel[] is an array of structures defined in Class "switch" which has fren class switch_port. Thus instances of class switch_port uses owner, to access members of class 'switch'. The structure Input_Channel contains a member of type list. The list stores the structures pointers of type here 'flit'. here in my program 'flit' is a valid pointer as printing flit gives following:
(gdb) print flit->source
$52 = {1, 3}
(gdb) print flit->destin 
$53 = {1, 0}
(gdb) print flit->type
$54 = 0

but..
(gdb) print owner ->Input_Channel[VChannel]->InputVC 
Cannot access memory at address 0x8      (why this at the middle of execution, all the lists and structures are defined at the compile time, its only the flits, that are created and deleted continuously during the program execution)
(gdb) print owner ->Input_Channel [VChannel]->Status
Cannot access memory at address 0x0

gdb) print owner ->Input_Channel 
$58 = {0x0, 0x80550d0, 0x8055100, 0x8055130, 0x8055160, 0x8055190, 
  0x80551c0, 0x80551f0, 0x8055220, 0x8055250}
(gdb) print owner ->Input_Channel[0] 
$59 = (<anonymous struct> *) 0x0
(gdb) print owner ->Input_Channel[1] 
$60 = (<anonymous struct> *) 0x80550d0 (what does this mean)
(gdb) print owner 
$61 = (switches *) 0x8055050

(gdb) print owner ->Input_Channel[VChannel]->flit_buffer.size()
Program received signal SIGSEGV, Segmentation fault.
0x0804c0d7 in std::list<flit_pkt*, std::allocator<flit_pkt*> >::begin (
    this=0xc) at /usr/include/c++/4.4/bits/stl_list.h:699
699          { return const_iterator(this->_M_impl._M_node._M_next); }
The program being debugged was signaled while in a function called from GDB.
GDB remains in the frame where the signal was received.
To change this behavior use "set unwindonsignal on".
Evaluation of the expression containing the function
(std::list<flit_pkt*, std::allocator<flit_pkt*> >::size() const) will be abandoned.
When the function is done executing, GDB will silently stop.


Please can anyone help me...please let me know if the question in not clear, as i am trying to put lots of information here..

---

### Post by dwhitney67 on 2010-02-15
No, I cannot help you.  I need to see how you are populating the Input_Channel array, and with what object (ie show the class declaration).

Obviously, you have not populated the array properly; if you had, then the program would not have crashed.

Your use of a friend class, 'switch_port', is also indicative that perhaps you flaw in your design.  You should avoid friend classes, and instead provide the proper interfaces within the class 'switch' to access member data.

So, post the following from your code.

[LIST=1]
[*]The 'switch' class
[*]The 'switch_port' class
[*]The declaration of Input_Channel
[*]How you are populating Input_Channel
[/LIST]

---

### Post by primenu on 2010-02-15
I am trying to implement wormhole routing here.
The fren switch_port class is thus used by switch to send the packets to its neighbour switch towards the destination:
```
switch_port::switch_port(switches *own)
{
        owner = own;
}
bool switch_port::eject_message(flit_pkt *flit, int *VChannel,int N1,int N2, int InputVC){
    int out = *VChannel;
    //cout<<"\nFlit_type: Received: "<<flit->type;
    if(flit->type == 1 ){
        if( owner->Input_Channel[N1]->Status == -1 ){// && owner->Input_Channel[N1]->flit_buffer.size()<flit_size){ 
            owner->Input_Channel[N1]->flit_buffer.push_back(flit);
            owner->Input_Channel[N1]->Status = 1;
            owner->Input_Channel[N1]->InputVC= InputVC;
            *VChannel = N1;
            return true;
        }else if(owner->Input_Channel[N2]->Status == -1 ){// && owner->Input_Channel[N2]->flit_buffer.size()<flit_size){ 
            owner->Input_Channel[N2]->flit_buffer.push_back(flit);
            owner->Input_Channel[N2]->Status = 1;
            owner->Input_Channel[N2]->InputVC= InputVC;
            *VChannel = N2;
            return true;
        }
    }else if(flit->type != 1 && owner->Input_Channel[*VChannel]->Status == 1 && owner->Input_Channel[*VChannel]->flit_buffer.size() < flit_size && owner->Input_Channel[*VChannel]->InputVC == InputVC){
        owner->Input_Channel[*VChannel]->flit_buffer.push_back(flit);    // push the flit into flitbuffer of the VC
        return true;
    }
    return false;    
}

In The update phase, the packets stored in the channel(I am using here Input_Channel) are then routed to the Outgoing channel(Output_Channel) in the switch(the head-packet is used for selecting route). In the communication phase the messages stored in the Outgoing channel are either routed to neighboring switch or the home node, :
void switches::update_switch(){
    
    for(int i=1; i < 10; i++){
        if(Input_Channel[i]->flit_buffer.size() > 0 ){
            if(Input_Channel[i]->flit_buffer.front()->type == 1){
                if(Channel_Selection(Input_Channel[i]->flit_buffer.front(), &Input_Channel[i]->OutputVC, i)){
                    Input_Channel[i]->flit_buffer.pop_front();
                }
            }else if(Input_Channel[i]->flit_buffer.front()->type == 0 && Output_Channel[Input_Channel[i]->OutputVC]->InputVC == i){
                if(Output_Channel[Input_Channel[i]->OutputVC]->flit_buffer.size() < flit_size){
                    Output_Channel[Input_Channel[i]->OutputVC]->flit_buffer.push_back(Input_Channel[i]->flit_buffer.front());
                    Input_Channel[i]->flit_buffer.pop_front();
                }
            }else if(Input_Channel[i]->flit_buffer.front()->type == -1  && Output_Channel[Input_Channel[i]->OutputVC]->InputVC == i){
                if(Output_Channel[Input_Channel[i]->OutputVC]->flit_buffer.size() < flit_size){
                    Output_Channel[Input_Channel[i]->OutputVC]->flit_buffer.push_back(Input_Channel[i]->flit_buffer.front());
                    Input_Channel[i]->flit_buffer.pop_front();
                    Output_Channel[Input_Channel[i]->OutputVC]->InputVC = 0;
                    Input_Channel[i]->Status = -1;
                    Input_Channel[i]->OutputVC = -1;
                }
            }
        }
    }    
}
void switches::eject_message(void){
//    flit_pkt *message;
    for(int i = 1; i < 10; i++){
        if(Output_Channel[i]->Status != -1 && Output_Channel[i]->flit_buffer.size() > 0){
            switch(i){
            case 1:
            case 2: 
                if(Output_Channel[i]->flit_buffer.front()->type == 1){
                    if( port_E->eject_message(Output_Channel[i]->flit_buffer.front(), &Output_Channel[i]->OutputVC, 5,6, i) == true){
                        //cout<<"\nVirtual Channel Assigned after sending to portE: "<<Output_Channel[i]->OutputVC;
                        Output_Channel[i]->flit_buffer.pop_front();
                    }
                }
                else if(Output_Channel[i]->flit_buffer.front()->type == 0 ){
                    if( port_E->eject_message(Output_Channel[i]->flit_buffer.front(), &Output_Channel[i]->OutputVC, 5,6, i) == true ){
                        Output_Channel[i]->flit_buffer.pop_front();
                    }
                }
                else if(Output_Channel[i]->flit_buffer.front()->type == -1 && port_E->eject_message(Output_Channel[i]->flit_buffer.front(), &Output_Channel[i]->OutputVC, 5,6, i)){
                    Output_Channel[i]->flit_buffer.pop_front();    
                    Output_Channel[i]->Status = -1;
                    Output_Channel[i]->OutputVC = 0;
                }
                break;
            case 3:
            case 4:
..............and so forth....
```i have attached the whole code..if it can make any sense..thanks in advance for any suggestions, I would really appreciate it

---

### Post by dwhitney67 on 2010-02-15
Your attachment is missing the simulate.cc and simulate.h files.

If I cannot build the product and run it through the debugger, then I cannot help.


P.S.  Is this your first C++ project?  Do you learn to program in C first?  There are many things you could improve in the code you supplied.

---

### Post by primenu on 2010-02-15
here is the other file..I have done some programming in c++ before but i a a learner, but that was quite some time ago. :(..In the process of debugging my code, I know, I have made it look even worse sorry for that..but I would appreciate if you make any comments on..
I have attached the sample trace file I am using..I know there are still things to do in the code..like when the message type is send or receive both have to be taken into account of instead of discarding message type 'recv'. The problem is the simulation completes when there are relatively(1000) fewer messages but when the number increase it crashes..

---

### Post by dwhitney67 on 2010-02-15
<edited>

Did you supply a different version of the code you originally posted?  I am unable to duplicate the segmentation violation.  The program runs to completion; even valgrind is happy that you freed all of the memory that was allocated.

Btw, unless absolutely needed, you should refrain from allocating on the heap.  For example, IMO, there is no need to allocate the 'startup' object.

You should also not include the run-loop of the application within the 'startup' constructor; put this in a separate method.  Similarly for the wrap up of your application; put what is necessary within a destructor method.

There's a lot of other things I would have done different, but being that this is my day off from work, I am electing to pursue other interests.


P.S.  Maybe it would have been helpful if you would have included the 'trace_file.txt' in the tar-files.

---

### Post by primenu on 2010-02-15
As I already mentioned, the simulation completes with the number of message fed into the program is small but with the increase in number of the messages like 20000 or so.. it gives segmentation fault, I can't figure out whats causing the problem..

---

### Post by Zugzwang on 2010-02-15
> **primenu said:**
> As I already mentioned, the simulation completes with the number of message fed into the program is small but with the increase in number of the messages like 20000 or so.. it gives segmentation fault, I can't figure out whats causing the problem..

Try running it with valgrind. Linux does not distinguish between a stack overflow and a "regular" segmentation fault. Probably you run out of stack space?

---

### Post by dwhitney67 on 2010-02-15
> **primenu said:**
> As I already mentioned, the simulation completes with the number of message fed into the program is small but with the increase in number of the messages like 20000 or so.. it gives segmentation fault, I can't figure out whats causing the problem..

Sorry for the late posting of this follow-up
> 
P.S. Maybe it would have been helpful if you would have included the 'trace_file.txt' in the tar-files.

Can you please supply this file?

---

### Post by primenu on 2010-02-15
Thanks for the reply..sorry if I look too dumb or?? but I couln't figure out how to fix this..i posted another thread with the same problem [http://ubuntuforums.org/showthread.php?t=1401543](http://ubuntuforums.org/showthread.php?t=1401543)
So if you even had time or can see what I was trying to do in my code..I will try to explain..
the msg_waiting_list stores the list of messages pending to be sent into the network(time_stamp, msg_size, destination), so when the channel is free then the message is popped from the list and divided into packets of size 8 units (in my program) and pushed into the channel. Inorder to avoid stack Overflow(??), when every waiting nodes trying big huge list of packets, I put a limit to the available size Channel buffer size, and wait until it is free, also at the receiving end, the packets are deleted immediately after they are received.. keeping track that the worm is kept intact.
At least this is what I tried to do.. but no success...Can you make any suggestions or am I missing something or lots of things here...

---

### Post by primenu on 2010-02-15
this is the trace file.the file is huge 15 MB. so i have edited to make it small, you could just replicate the lines if you like..

---

### Post by dwhitney67 on 2010-02-15
Well, your app is dying because of the excessive recursion taking place in sim_stop().

Recheck your algorithm to ensure that eventually your exit criteria is met.

---

