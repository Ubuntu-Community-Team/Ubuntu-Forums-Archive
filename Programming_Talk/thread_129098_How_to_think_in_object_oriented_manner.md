---
title: "How to think in object oriented manner ?"
date: 2006-02-12
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-12
I was a C programmer till now. I am learning python now. I want to learn the concepts of Object oriented programming. I have read books but never done any real life project to get a feel it.

Now i am doing a project in python but my inability to think in object oriented way makes my python programs quite modular. I try to identify classes but after a while I realize that i just have 2 or 3 .py files and all of them get big. I tend to use lot of code in just one file which is not good. And then if I try to slplit code in various files and classes I mes things up. Mostly, the issue of variable being not able to access from other file crops up.

Do you guys have tips for novice coders like me.

All your help is greatly appreciated.

thanks

---

### Post by LordHunter317 on 2006-02-12
Start by defining your data structures first.  What are you trying to model?  What information about the model do you need to store?

Don't do this in code.  Do it on paper.  If you need structure, check out UML.   Look at use case diagrams, activity diagrams, and then class diagrams.  

After that, figure out what operations need to be performed on these data structures.  I'll start with an example at this point.  Let's say I'm doing a traffic simulation of a busy intersection.  One of the things I might need to model is a car.  The information I might need to store about a car is it's speed, current lane position, etc.

Behaviors might include braking, changing lanes, etc.  From here, I can define my algorithims to perform these operations on the data.

Once you have all that, then you can define your actual classes.

Classes should be defined based primarily on behaviors: *operations* you want to perform on the data, instead of the data itself.

Note a behavior can be anything.

For example, in the project I'm currently writing, I have a class who's sole purpose is to manage a connection.  It creates a connection when necessary, and deletes it when the object is no longer used.

The operations it provides are queries through that connection.  I have a another class that does the exact same thing, but managing a DB transaction instead.  It provides additional operations to control commiting or rolling back the transaction.

These classes have nothing to do with the actual data I'm processing, they just model a useful set of behaviors.

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=krypto_wizard]I was a C programmer till now. I am learning python now. I want to learn the concepts of Object oriented programming. I have read books but never done any real life project to get a feel it.

Now i am doing a project in python but my inability to think in object oriented way makes my python programs quite modular. I try to identify classes but after a while I realize that i just have 2 or 3 .py files and all of them get big. I tend to use lot of code in just one file which is not good. And then if I try to slplit code in various files and classes I mes things up. Mostly, the issue of variable being not able to access from other file crops up.

Do you guys have tips for novice coders like me.

All your help is greatly appreciated.

thanks[/QUOTE]

Well, it sounds more like you just have a problem splitting your program into manageable sized units, rather than having anything to do with "objects".

In most of the python programs I write, I tend to write a lot more functions than classes.  Objects are really only useful when you have some sort of state.  Some programs do not lend themselves particularly well to that model, so don't try to force it.

What I think you might want to try to do is to group related things together in the same modules.  Try to think, "Would these functions or classes be useful in another program I might want to write later?"  Don't over-analyse, though.  You can always go back later and factor out common code once you get a practical feel for what will be useful to reuse.  Putting that common code in a module is probably the best way to partition your programs in python.

If you find yourself having issues with global variables, you have to stop and think if you *really* want the variable to have an effect on an entire module.  If so, you can access them like any other names in a module.  If not, it may make more sense for the setting to be a parameter to a function or the state of some object.

---

### Post by Vegettex on 2006-02-13
Well every function in your application shouldn't be any larger then approx an a4 sheet. And every function should be in it's own class. For example if you want to draw a multigraph bar. Then it would be best if you create a class Graph which makes x instances of the class Bar. Graph should also be able to set the sizes of the bars so Bar should have some functions like Bar.update and Bar.setSize. Just a short example in the early morning ;)

---

### Post by thumper on 2006-02-13
[QUOTE=Vegettex]Well every function in your application shouldn't be any larger then approx an a4 sheet. [/QUOTE]
I agree with this.  It keeps things managable, and also useful to be able to print things out and look at them away from the computer.

[QUOTE=Vegettex]And every function should be in it's own class.[/QUOTE]
Don't agree with this.  This is the sort of things that Java programmers end up doing because in Java you have to do it that way.

As **cwaldbieser** mentioned, not all functions need state, so it does not make sense to put all functions into a class.  Python has modules to keep related functions together, you don't have to use a class.

Kudos to **LordHunter317** for his helpful descriptive post :)

---

### Post by LordHunter317 on 2006-02-13
[QUOTE=cwaldbieser]What I think you might want to try to do is to group related things together in the same modules.  Try to think, "Would these functions or classes be useful in another program I might want to write later?"[/quote]That's a bad way of organizing code, pretty much always, unless your intent is to write a shared-library.  You should be asking, "Is there a logical or semantical relationship between this functions" and using that to organize.

> You can always go back later and factor out common code once you get a practical feel for what will be useful to reuse.Simpler: if you write the same code twice (or certainly three times) it goes in its own method.  Problem solved.  This is a 80/20 rule (something like "%" + string "%" makes no sense in it's own method unless you're using a "pure" functional language) but a good one to follow.  It tends to lead to simpler functions, clearer intent, and better design.  It's usually eaiser to determine common functionality by seeing it occur, instead of trying to anticpate it.

This is the rule I've been following on my last project, to great success.  It's made resource management eaiser and clearer.

> If you find yourself having issues with global variables, you have to stop and think if you *really* want the variable to have an effect on an entire module.If you're having an issue with global variables, just stop using them.  They're very rarely necessary, just like singletons are.

One should stop and think, then go for a walk, then think again, before creating either.

[quote=Vegettex]And every function should be in it's own class.[/quote]No, that's illogical.  No one does that.  And one should tend for non-member, non-friend functions wherever possible, in all languages that let you do so.  They actually enhance encapsulation.

That's one reason C++ does the STL algorithms this way.  It leads to more correct code, because non-member, non-friend functions can only rely on a class's interface, not it's implementation.

---

### Post by krypto_wizard on 2006-02-13
thanks to everybody for their comments

---

### Post by jerome bettis on 2006-02-13
read this book  [http://archive.eiffel.com/doc/oosc/](http://archive.eiffel.com/doc/oosc/)

no joke, go buy it and read it.

do it

---

### Post by krypto_wizard on 2006-02-14
Thanks for all the replies. I will try to brief out the problem I am tackling and also my solution. You can tell me if I am on a right track.

I am simulating a bit torrent file sharing mechanism. There are thousands of nodes in the swarm, a tracker and original seed(Server). I have to mimic that nodes exhange part of the file with other nodes to complete their file download. In addition, group of nodes forma an alliance to share information reliably. For ex if node 2,5,8 are part of an alliance, if 5 get a new packet he will pass it on to 2 and 8. This process is also done by all members of the allainces. I am just writing a standalone simulation and not an application based on threads. 

I have identifies nodes as one class. With attributes such as Node ID, Node IP address, Node Uplink and downlink speed, Share ratio in it, I think this is worth abstracting. The second class was Alliance, which contains alliance_id, num_of_node_in_ alliance, node_list_in_alliance etc.

Now my question comes how to abstract other entities like tracker. A Tracker has list of all the nodes in the system, their arrival time in the swarm, list of peer nodes (for each node) etc. I thought my main program (in python) acts as Tracker functionality. 

At this point I am not comfortable as how to deal with classes. How to go about the design. Every help is greatly appreciated. 

Sorry for long post, but I tried to abstract thins as suggested by LordHunter317 but kinda got confused. Thanks for your time.

---

### Post by LordHunter317 on 2006-02-14
You're on the right track, but a few notes.  

Information about an object should be universal to all instances of that object.  If it doesn't apply in all cases, you should create a new object that does, using composition (term for creating a class that contains other classes as members).

[QUOTE=krypto_wizard]I have identifies nodes as one class. With attributes such as Node ID, Node IP address, Node Uplink and downlink speed, Share ratio in it, I think this is worth abstracting.[/quote]Possibly.  Think about dat first.  As I said, write it on paper.  Make sure what you're including is what you need.  The data doesn't necessarily need to be a strict mapping of the real-world information.  If some information is unnecessary for your application  or is better modeled differently, do it that way.

> A Tracker has list of all the nodes in the system, their arrival time in the swarm, list of peer nodes (for each node) etc. I thought my main program (in python) acts as Tracker functionality.If it were me, I'd create a class called TrackerEntry.  I'm not familiar with Python, but in C#, it'd be something like:```
class TrackerEntry {
    private Node node_;
    private DateTime arrivalTime_;
    private DateTime leaveTime_;
}
```With appropriate constructors and properties and such as needed.  This class need not be seen by anything but the tracker.   Depending on what behaviors a tracker supports, you may be able to hide the fact you're using this class internally.  For example, to add a node to a tracker and use the current date/time for arrival, you'd write:```
class Tracker {
     private IList<TrackerEntries> members_;

     public AddNode(Node node) {
         TrackerEntry entry = new TrackerEntry(node, DateTime.now);
         members_.Add(entry);
     }
}
```And no one is any the wiser.  This is practicing good encapsulation, or information hiding.  The point of encapsulation is to enforce rules on "users" of your class (code that calls your class).

Explaining exactly what you need to model in this simulation would be useful.  I would start with modeling nodes, but it sounds like you need to model relationships between nodes as well (how much data shared between them, etc).  That information would belong to a class, likely.  It would be a good candiate for a directed graph most likely, but it's hard to tell without exact details on what you're doing.  

Note that whever possible, you should prevent direct access to your data members and instead provide operations on them, like I did above.  Instead of giving them access to the members_ list, I just give users the ability to add.  This controls access to your data and helps prevents bugs.

Note in some situations, a "record" class that consists of just fields with perhaps accessors (methods that return a stored value in a class) are perfectly appropriate.  This is usually the case when the data is just intended to be displayed (e.g., a record for a webpage) or design dictates that it's clearer to put the operations elsewhere.

---

### Post by krypto_wizard on 2006-02-14
Thanks LordHunter317 for your input. I will expatiate more on my code.

There will be hundreds of nodes in the swarm. They exchance pieces of files with each other. Suppose they are all trying to share Ubuntu.iso file which has 100 pieces, they all have a common aim to get those 1oo pieces and get the file Ubuntu.iso. The instances of the node class interact among themselves for the 
"boolean[100] FileList", where true represents the file block procured and false represents not procured. There is one node called SEED which has all 100 pieces initially. It starts giving out to other nodes, nodes in turn share it with other and all the nodes form a strong mesh of network. A group of 6-8 nodes together forms an allaince for their mutual benefit. If one node gets a new packet in the alliance he passes it on to its allaince members. So allaince class has attributes as ID, list of nodes in allaince, number of nodes in allaince,

Tracker ( as name suggest does the job of keeping track of nodes) does accounting job of keeping list of all the nodes in the swarm, when they came, when they left etc.

The simulation runs untill all the nodes in the swarm procure all the 100 pieces of the file. This I have done in my main() using a while loop.

As of now, I have identified nodes as one class, alliance as second. As you suggested tracker should be one class.

my psuedo code
```

main()
{
   file input

   while(file downloading not finished for everyone)
   {
         for each node in swarm
         {
                Performs file exhange
                       Do Downloading
                       Do Uploading

        }

        system time++
        if (donwload finished for everone)
        {
            flag = true;
        }
   }

   print Statistics

   program ends
}

```

EVery help is greatly appreciated.

Thanks

---

### Post by LordHunter317 on 2006-02-14
Ok, you're on the right track, I think.  

Any rate, I assume this simulation includes such things as connects and disconnects, right?  If so, I would suggest modeling each node with a state machine.

A state machine is an entity that has a fixed number of states, and a fixed set of transitions between them.  It can only be in one state at a time.  Now, a node can be JOINING, CONNECTED, COMPLETED, DISCONNECTED, etc. 


You'll have each node perform a single "operation" per unit time.  What action a node takes is dependent on it's state.  For example, a node in state JOINING will connect and join the tracker in its first time unit, and then transition to the CONNECTED state.  A node that recieves all 100 blocks will transition to the COMPLETE state in whatever time unit it receives the final block.   

This may also be overkill.  OTOH, it will force you to think about your design, and it makes it easy to draw a graph of the states and the nodes between them.


The way I would work this is focus primarily on the nodes in the swarm.  I'd keep a collection of all the nodes (an array will be find for this purpose, a linked list may be better if you intend to add/delete during the simulation.  I'm not sure I see the need for that, though).  

For each unit time (your main loop), I'd enumerate the list and ask each node to perform it's "action", whatever that may be.  There would be a single method action() you'd call that would perform whatever the node would perform in that state.  That would include connecting to other nodes, sharing data with their allies, etc.  

Interally, a node would keep all the information it needs to perform these actions.  This means it'd keep a list of all alliances it is a member of, so that when it recieves data, it can automatically pass it on to each of it's nodes.  Calling action() would cause the node to do this automatically.  It would do this by calling a method on the alliance called give_to_members() or similar.  The alliance would then enumerate it's internal list of members and pass the data to each node, by calling a receive_from_alliance() method (or perhaps a generic receive() method, if you don't care about the source).  Entry and exit from the alliance would be provided by add/delete methods.  That way, a node doesn't care about who else is a member of the alliance when it passes data.  This was the whole "providing operations" thing I was talking about before: the node doesn't care about or even know about other nodes in the alliance, just the fact that it can send data to it and recieve data from them.

Also, a node would update the tracker if necessary, etc.

After doing the nodes, I would update the tracker state as well, if it has any bookkeeping that needs to be performed that doesn't occur from node actions.

Then, you restart the loop.

Depending on how you implement things, the main loop could be encapsulated in a state machine as well, that drives the simulation.  This depends on how complicated your simulation logic is.

I can post some pseudo-code if you like, but hopefully that gives you a better idea.

---

### Post by krypto_wizard on 2006-02-15
Thanks LordHunter317 for all your feedback. I like the idea of keeping the states for the nodes. I get most the things you said. 

I am just trying to visualize how the different objects interact with each other.
If I classify classes as per your views, we have nodes, alliances, tracker as three main classes. I tried to draw the interaction of the instances of the above mentioned classes.....I think I get a little confuse here.


I have the following

class node{
  all the parameters related to nodes viz id, ip address, arrival time etc
  all the methods viz
       get_share_ratio()
       TBD...
}

class alliance{
   all the parameters viz alliance id, num_of_nodes, array_of_nodes_in_alliance
    all the functions 
}

class Tracker{
   parameters such as ... list_of_all_nodes, 
   functions (...I haven't identified as yet)
}

Now I want to be able to visualize how the main function would call these classes as these classes are embedded in each other. For example node class contains list of alliance it is member of. Alliance class contains list of nodes etc. Tracker class contains both nodes and alliances.

Could you put a high level psuedo code (C++ main function) for the above case. I know its kinda asking for too much but your every help is greatly appreciated.

Thanks

---

### Post by LordHunter317 on 2006-02-15
[QUOTE=krypto_wizard]Now I want to be able to visualize how the main function would call these classes as these classes are embedded in each other.[/quote]It doesn't.  All it calls is node.action(), or similar.  That calls whatever it'd need to call.

> Could you put a high level psuedo code (C++ main function) for the above case. I know its kinda asking for too much but your every help is greatly appreciated.Sure, here's a rough sketch:
```
class node:
    def startup_action(self):
        self.tracker.connect(self)
        self.state = "CONNECTED"

    def connected_action(self):
        self.peers.append(self.tracker.get_new_peers(self.peers))
        for peer in self.peers:
            received_chunk = peer.send_a_chunk(outstanding_chunk)         
            self.outstanding_chunks.remove(removed_chunk)
            self.recieved_chunks.append(received_chunk)
            self.alliance.send_to_peers(received_chunk)

    state_func_map = { "STARTUP" : startup_action,
                                "CONNECTED" : connected_action,
                                "COMPLETED" : completed_action
                              }

    def __init__(self, tracker):
        self.state = "STARTUP"
        self.peers = []
        self.tracker = tracker
        self.outstanding_chunks = range(100)
        self.recieved_chunks = []

    def action(self):
        state_func_map[self.state](self)
```There's the start of a node class.  Your main loop would just call action() on all the nodes in a list:```
for node in nodes:
    node.action()
```action() uses the state_func_map to map a state to an action to call.  This makes the dispatch easy.  The corresponding function performs whatever action is necessary, and then changes state if appropriate.  By maintaining references to the other objects, you can perform the necessary calls to other objecst in turn.

Note I define behaviors: when a node wants to get data from another node, it calls send_a_chunk on the other node and passes it a list of chunks it wants.  If the node can provide it a chunk, it passes back the number of the chunk it can provide, and the calling node adds that chunk to it's received list and deletes it from it's desired list.  Note some error checking is needed there, as the value passed to [].remove() must be a valid index.

Then, if it got a chunk, it passes it on to it's alliance, by calling alliance.send_to_peers().  The alliance class might look like:```
class alliance:
    def __init__(self):
        self.nodes = []
 
    def send_to_peers(self, chunk)
        for node in self.nodes:
             node.recieve_chunk(chunk)
```And in that manner, it passes the chunk to all members of the alliance.

One thing to note that's a major operation: when you define nodes and the links between them, you're creating a graph. Each node is storing an adjacency list of nodes in the graph; an adjacency list is a list of all nodes another node is connected to; a connection between nodes is called an edge.  Each unique adjacency list only needs to be visited once.  This means that you should probably write your code so that when node A sends to node B, node B also asks node A for any data it needs and then marks that it has talked to node A in that time step.  That way, when node B is visited, it doesn't have to visit A again, as that would be redundant.  This prevents you from visiting each edge twice.  If you have lots of edges, that could be a significant saving.

---

