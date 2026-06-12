---
title: "what's this valgrind error about?"
date: 2009-03-05
forum: Programming Talk
---

### Post by tneva82 on 2009-03-05
```
==11178== 1,351,936 bytes in 5,281 blocks are indirectly lost in loss record 26 of 27
==11178==    at 0x402505E: operator new[](unsigned) (vg_replace_malloc.c:268)
==11178==    by 0x804F849: player::player() (player.cpp:10)
==11178==    by 0x8056F52: server::listen() (serverListen.cpp:148)
==11178==    by 0x804FF79: server::start() (server.cpp:188)
==11178==    by 0x804D222: main (mainserver.cpp:10)
```

```
player.cpp:10 is userName=new char[256];
``` 

Similar error for line 9 which is of similar type.

Is it because said constructor doesn't have delete[] clause for it(it lies in destructor)? Or because new player is created like this:

```
playerList.push_back(new player());
```

where playerList is vector<player*> playerList.

Just found the valgrind and am now debugging through code.

And while we are at memory issues why can't I do something like this:

```
if(array!=NULL) {
   delete[] array;
}
```

I thought that was way to determine wether there's any memory allocated to array via new but that just causes segmentation errors same as if there wasn't if statement to begin with.

Edit: and second odd error I get with valgrind:

=11235== Conditional jump or move depends on uninitialised value(s)                                                                                      
==11235==    at 0x4343003: strtok (in /lib/tls/i686/cmov/libc-2.8.90.so)                                                                                  
==11235==    by 0x804FF79: server::start() (server.cpp:188)                                                                                               
==11235==    by 0x804D222: main (mainserver.cpp:10) 

server::start function is:

```

void server::start() {
  running=true;
  printf("hep!!!\n");
  while(running) {
    listen();
    mainAction();
    //replyToClients();   
  }
}

```

why listen() depends on uninitialised value(s)? As far as I see as long as running is true(definetly initialised since that's just right above it) it performs listen. I get tons of these error messages for the very same spot(ie listen() line). What's up with that?

---

### Post by monkeyking on 2009-03-05
whats the type of userName?
just post all your code,
it will make it easier

---

### Post by tneva82 on 2009-03-05
> **monkeyking said:**
> whats the type of userName?
just post all your code,
it will make it easier

char *userName. I thought it was clear enough when it's allocated like userName=new char[256]; :D sorry about that.

Would post all if there weren't literally hundreds of lines of code. I don't think anybody would be interested in sorting through all that.

BTW I get tons of indirect block losses on this(or other similar lines):

playerList.push_back(new player());

So definetly SOMETHING wrong in there but what? Not fun that the longer the program run the more blocks is lost indirectly in above line.

Edit: Heck that line + the listen() call of "uninitialised value(s)" are right about 99% of errors valgrind provides. Remaining 1% are other of similar type to that push_back call.

---

### Post by tneva82 on 2009-03-05
Excelent. Have managed to trim down MOST of the memory leaks down. Handy tool for certain. Still few issues. I'll try to put all relevant code here. I bold the lines where error comes up.

==12877== Conditional jump or move depends on uninitialised value(s)                                                        
==12877==    at 0x4026190: index (mc_replace_strmem.c:160)                                                                  
==12877==    by 0x804F5D5: player::readNetwork(char*) (player.cpp:54)                                                       
==12877==    by 0x8057625: server::listen() (serverListen.cpp:172)                                                          
==12877==    by 0x804FFD9: server::start() (server.cpp:211)                                                                 
==12877==    by 0x804D222: main (mainserver.cpp:10) 

```
int player::readNetwork(char *answer) {
  int result;
  int  bytesRcvd = 0;
  
  if(SDLNet_CheckSockets(mySet, 1)>0) {
    if(SDLNet_SocketReady(mySocket)!=0) {  
     ** do {**      
	result=SDLNet_TCP_Recv(mySocket, answer+bytesRcvd, 1);
      
	if(result==0) {
	  SDLNet_TCP_DelSocket(mySet,mySocket);
	  SDLNet_TCP_Close(mySocket);
	  return 0;
	}
	bytesRcvd+=result;
      } while(!strchr(answer, '\n') );
      //printf("Answer is: %s\n", answer);
    }  
    return result;
  }
  return -1;

}
```

```
int server::listen() {
  for (int i=0;i<clientsConnected; i++) {
    buf=new char[MAX_PACKET_SIZE];
    buf[0]=' '; // this was just desperate attempt if this would mean it's initialised. Also tried strcpy(buf, " ");
    **if(playerList[i]->readNetwork(buf)>0) {**
      for(int j=0;j<messages.size();j++) {
	delete[] messages[j];
      }
      messages.clear();
      buf=strtok(buf, "*");
      printf("%s\n", buf);
      while(buf!=NULL) {
	messages.push_back(buf);
	buf=strtok(NULL, "*");
      }
      
      for(int j=0;j<messages.size();j++) {
	resolvePlayerMessages(messages[j], i); 
      }
    }
    delete[] buf;
  }
```

Second error:

==12877== Use of uninitialised value of size 4                                                                              
==12877==    at 0x4342FE9: strtok (in /lib/tls/i686/cmov/libc-2.8.90.so)                                                    
==12877==    by 0x804FFD9: server::start() (server.cpp:211)                                                                 
==12877==    by 0x804D222: main (mainserver.cpp:10) 

And:

==12877== Conditional jump or move depends on uninitialised value(s)                                                        
==12877==    at 0x4342FEC: strtok (in /lib/tls/i686/cmov/libc-2.8.90.so)                                                    
==12877==    by 0x804FFD9: server::start() (server.cpp:211)                                                                 
==12877==    by 0x804D222: main (mainserver.cpp:10)     

Both in following code:

```
void server::start() {
  running=true;
  printf("hep!!!\n");
  while(running) {
    **listen();**
    mainAction();
    //replyToClients();   
  }
}  
```

And then last few memory leaks. This one repeats twice.

==12877==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)                                                                                               
==12877==    by 0x41A6510: SDLNet_AllocSocketSet (in /usr/lib/libSDL_net-1.2.so.0.0.7)                                                                    
==12877==    by 0x804F897: player::player() (player.cpp:13)                                                                                               
==12877==    by 0x8057442: server::listen() (serverListen.cpp:151)                                                                                        
==12877==    by 0x804FFD9: server::start() (server.cpp:211)                                                                                               
==12877==    by 0x804D222: main (mainserver.cpp:10) 

```
player::player() {
  name=new char[256];
  userName=new char[256];
  nextMessage=new char[MAX_PACKET_SIZE];
  strcpy(nextMessage, "");
  **mySet = SDLNet_AllocSocketSet(1);**
}
```

However mySet IS freed in destructor. Surely it would complain same about name etc if somewhere players destructor isn't called ever? Might this be fault in SDL_Net instead?

```
int server::listen() {
  char *buf;
  vector<char*> messages;
  **playerList.push_back(new player());**
  if(playerList[clientsConnected]->addSocket(SDLNet_TCP_Accept(readSocket))) {
    if(clientsConnected<MAX_CONNECTIONS) {
      printf("Connection established!\n");
      clientsConnected++;
    } else {
      char buf[5];
      sprintf(buf, "%i", GNOCONNECTIONSAVAILABLE);
      playerList[clientsConnected]->addMessage(buf);
      delete playerList[clientsConnected];
      playerList.pop_back();
    }
  } else {
    delete playerList[clientsConnected];
    playerList.pop_back();
    //playerList.erase(playerList.begin()+clientsConnected);
  }
```

And this repeats twice:

==12877== 350 bytes in 1 blocks are possibly lost in loss record 3 of 4
==12877==    at 0x402505E: operator new[](unsigned) (vg_replace_malloc.c:268)
==12877==    by 0x80575F6: server::listen() (serverListen.cpp:170)
==12877==    by 0x804FFD9: server::start() (server.cpp:211)
==12877==    by 0x804D222: main (mainserver.cpp:10)

```
for (int i=0;i<clientsConnected; i++) {
    **buf=new char[MAX_PACKET_SIZE];**
    buf[0]=' ';
    if(playerList[i]->readNetwork(buf)>0) {
      for(int j=0;j<messages.size();j++) {
	delete[] messages[j];
      }
      messages.clear();
      buf=strtok(buf, "*");
      printf("%s\n", buf);
      while(buf!=NULL) {
	messages.push_back(buf);
	buf=strtok(NULL, "*");
      }
      
      for(int j=0;j<messages.size();j++) {
	resolvePlayerMessages(messages[j], i); 
      }
    }
    delete[] buf;
  }
```

I think that's pretty much all code relevant there. Some variable definitions:

```
 //player.h
  TCPsocket mySocket;
  SDLNet_SocketSet mySet;
  char *nextMessage;
  char *name;
  char *userName;

```

However there's been DEFINETLY "some" improvement. Seems code was one heck of a memory leaker before. Now about 1.5kb lost. Not that bad though about 1.5kb too much. Atleast I shoudln't run out of memory while testing and debugging!

---

### Post by tneva82 on 2009-03-05
Almost there. Now leak summary shows only:

==9033== LEAK SUMMARY:
==9033==    definitely lost: 12 bytes in 1 blocks.
==9033==    indirectly lost: 4 bytes in 1 blocks.


Woot!

However now the program doesn't work without valgrind...Darn!

What sort of error are we talking about when valgrind allows to run program without errors but without it nothing happens when I try to send message except connection is established?

---

### Post by dwhitney67 on 2009-03-05
I guess my system runs in a different universe.  Valgrind reports issues when I attempt something like:

```

char* buf = new char[20];
...
buf = strtok(buf, "*");

while (buf)
{
  ...
  buf = strtok(0, "*");
}

delete [] buf;

```

Thus I have learned to write the code above as:
```

char* buf = new char[20];
char* tmp = buf;
...
tmp = strtok(tmp, "*");

while (tmp)
{
  ...
  tmp = strtok(0, "*");
}

delete [] buf;

```
The 'delete' method requires the original pointer that was allocated by 'new'; not NULL, which is what buf will be if the first style of code is used.  But hey, that's what I have observed on my system.  It may be different on yours.

---

### Post by tneva82 on 2009-03-05
> **dwhitney67 said:**
> The 'delete' method requires the original pointer that was allocated by 'new'; not NULL, which is what buf will be if the first style of code is used.  But hey, that's what I have observed on my system.  It may be different on yours.

Dunno why it didn't complain about that(computers are funny things. You can never be sure with them :D) but anyway there were the errors.

Though I figured even better solution few moments ago. Why bother with temp variable when I can simply push into the vector strtok's output to begin with? No need to mess with temp variable and technicly should even result in slightly faster program(albeit not noticably so but everything counts :D)! Got it working right there and all the memory leaks around there went away just like that. Damn I feel stupid for not making it like this in a first place(however I am starting to learn to love the vector class. Positively wonderful class that one. Helps with the program a LOT)

Anyway just 2 leak error messages left with the SDLNet_allocsocketset functions. Dunno what's up with those. If I would get complains also about the 3 char* arrays I would guess there's lack of destructor call somewhere but since that's not the case...Well makes me think SDLNet code might have bug...

==9710== 16 (12 direct, 4 indirect) bytes in 1 blocks are definitely lost in loss record 2 of 2
==9710==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==9710==    by 0x41D44F2: SDLNet_AllocSocketSet (in /usr/lib/libSDL_net-1.2.so.0.0.7)
==9710==    by 0x804F913: player::player() (player.cpp:13)
==9710==    by 0x805746E: server::listen() (serverListen.cpp:152)
==9710==    by 0x8050055: server::start() (server.cpp:211)
==9710==    by 0x804D29E: main (mainserver.cpp:10)

Atleast now memory leaks are MUCH less severe(first time I ran valgrind result was positively horrendous. Turns out I had misunderstood working of vector class big time :D I have also managed to sort the network code easier to use and now there's lot less tossing around pointers to common stuff as I figured out better way to do it.

---

