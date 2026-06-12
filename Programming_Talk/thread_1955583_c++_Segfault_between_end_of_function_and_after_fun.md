---
title: "c++ Segfault between end of function and after function"
date: 2012-04-09
forum: Programming Talk
---

### Post by compiz addict on 2012-04-09
Edit: ****! I accidentally posted it as solved! I'm just going to bump it until I get an answer then...
Edit: [PrettyMuchSolved]


What situation could cause me to experience a segfault in between the last thing a function does, and after the function is called?

I am outputting text right at the very end of a function (right before that last closing bracket), and then after the function is called, and it looks a little something like this:
Before end of funcion...
Segmentation fault


Here's my code below (well, the portion of it that I think the problem is in at least - lots of code in this project):

The function I'm talking about is called getStickFigures()

```

void doNetworkStuff() {
  if (is_server==true) {
    getPackets();
    sendStickFigures();
  }
   if (is_client==true) { 
    sendStickFigure();
    printf("getStickFigures();\n");
    getStickFigures();
    printf("after getStickFigures();\n"); // This is never displayed
  }
}

```

```

int getStickFigures() {
  int theStickId, rint[19];
  for (int i=0; i<64; i++) {
		if (SDLNet_UDP_Recv(sd, p))
		{
			printf("UDP Packet incoming\n");
			printf("\tChan:    %d\n", p->channel);
			printf("\tData:    %s\n", (char *)p->data);
			printf("\tLen:     %d\n", p->len);
			printf("\tMaxlen:  %d\n", p->maxlen);
			printf("\tStatus:  %d\n", p->status);
			printf("\tAddress: %d %d\n", p->address.host, p->address.port);
			
			char *test[sizeof(strtok((char *)p->data, " "))];
			test[0] = strtok((char *)p->data, " ");
			if (strcmp(test[0], "stickman")==0) {
			  test[1] = strtok (NULL, " ");
			  test[2] = strtok (NULL, " ");
			  test[3] = strtok (NULL, " ");
			  test[4] = strtok (NULL, " "); rint[4]=atoi(test[4]);
			  test[5] = strtok (NULL, " "); rint[5]=atoi(test[5]);
			  test[6] = strtok (NULL, " "); rint[6]=atoi(test[6]);
			  test[7] = strtok (NULL, " "); rint[7]=atoi(test[7]);
			  test[8] = strtok (NULL, " "); rint[8]=atoi(test[8]);
			  test[9] = strtok (NULL, " "); rint[9]=atoi(test[9]);
			  test[10] = strtok (NULL, " "); rint[10]=atoi(test[10]);
			  test[11] = strtok (NULL, " "); rint[11]=atoi(test[11]);
			  test[12] = strtok (NULL, " "); rint[12]=atoi(test[12]);
			  test[13] = strtok (NULL, " "); rint[13]=atoi(test[13]);
			  test[14] = strtok (NULL, " "); rint[14]=atoi(test[14]);
			  test[15] = strtok (NULL, " "); rint[15]=atoi(test[15]);
			  test[16] = strtok (NULL, " "); rint[16]=atoi(test[16]);
			  test[17] = strtok (NULL, " "); rint[17]=atoi(test[17]);
			  test[18] = strtok (NULL, " "); rint[18]=atoi(test[18]);
			  test[19] = strtok (NULL, " "); rint[19]=atoi(test[19]);
			  
			  for (int i=4; i < 20; i++) {
			    printf("rint[%d]=%d",i,rint[i]);
			  }
			  
			  theStickId=atoi(test[1]);
			  stickman[theStickId].position.x=atoi(test[2]);
			  stickman[theStickId].position.y=atoi(test[3]);
			  std::cout << "Right before the input functions...\n";
			  stickman[theStickId].left_arm.setPoints( rint[4],rint[5],rint[6],rint[7] );
			  stickman[theStickId].right_arm.setPoints( rint[8],rint[9],rint[10],rint[11] );
			  stickman[theStickId].left_leg.setPoints( rint[12],rint[13],rint[14],rint[15] );
			  stickman[theStickId].right_leg.setPoints( rint[16],rint[17],rint[18],rint[19] );
			  std::cout << "asdfasdfasdf\n";
			}
			std::cout << "lastpartofif\n";
		}
		std::cout << "beforeendofor\n";
	}
	std::cout << "absoluteendoffunction\n"; // This is displayed.
}

```

---

### Post by nathan.the.sane on 2012-04-09
My guess would be you wrote past the end of one of your arrays, thus overwriting the address the function was supposed to return control to. In other words, classic buffer overflow. I still haven't figured out everything that's going on here though, so I could be wrong.

---

### Post by compiz addict on 2012-04-09
Right, yeah. I was so frustrated over my previous errors I forgot that -1 rule...

Anyway, it's still having a problem. The problem is in between where it outputs "absoluteendoffunction" and after the function getStickFigures(); is called. Here's all the code in networking.h:


```

bool is_server=false;
bool is_client=false;
int packCount;
std::string ip;
std::string port;
	UDPsocket sd;
	IPaddress srvadd;
	UDPpacket *p;
	int quit;
	
class aClient {
  public:
    int client_ip;
    int client_port;
    int client_stick;
};

std::vector<aClient> clients(0);

int getClientStick(int teh_c_ip, int teh_c_port) {
  for (int i=0; i < clients.size(); i++) {
    if (clients[i].client_ip==teh_c_ip && clients[i].client_port==teh_c_port) {
      return clients[i].client_stick;
    }
  }
  return -1;
}
//This doesn't work, and will probably use TCP anyway
int connectToServer(char *host, char *port) {
 
	/* Initialize SDL_net */
	if (SDLNet_Init() < 0)
	{
		fprintf(stderr, "SDLNet_Init: %s\n", SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
 
	/* Open a socket on random port */
	if (!(sd = SDLNet_UDP_Open(0)))
	{
		fprintf(stderr, "SDLNet_UDP_Open: %s\n", SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
 
	/* Resolve server name  */
	if (SDLNet_ResolveHost(&srvadd, host, atoi(port)) == -1)
	{
		fprintf(stderr, "SDLNet_ResolveHost(%s %d): %s\n", host, atoi(port), SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
 
	/* Allocate memory for the packet */
	if (!(p = SDLNet_AllocPacket(512)))
	{
		fprintf(stderr, "SDLNet_AllocPacket: %s\n", SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
	
	
		p->data=(Uint8 *)"connect";
		p->address.host = srvadd.host;	/* Set the destination host */
		p->address.port = srvadd.port;	/* And destination port */
 
		p->len = strlen((char *)p->data) + 1;
		SDLNet_UDP_Send(sd, -1, p); /* This sets the p->channel */
//SDLNet_FreePacket(p);
//SDLNet_Quit();
 is_client=true;
	return EXIT_SUCCESS;

//return returnTeh;
}

int becomeAServer() {
  printf("Ititializing SDLNet...\n");
  	if (SDLNet_Init() < 0)
	{
		fprintf(stderr, "SDLNet_Init: %s\n", SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
 
  printf("Opening UDP port %s\n", port.c_str());
	if (!(sd = SDLNet_UDP_Open(  atoi( port.c_str() )  ) ))
	{
		fprintf(stderr, "SDLNet_UDP_Open: %s\n", SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
 
  printf("Allowcating packet...\n");
	if (!(p = SDLNet_AllocPacket(512)))
	{
		fprintf(stderr, "SDLNet_AllocPacket: %s\n", SDLNet_GetError());
		exit(EXIT_FAILURE);
	}
	
	
	is_server=true;
	printf("Well, this part should work...\n");
	return EXIT_SUCCESS;
}


int getPackets() { // function for the server
  
for (int i=0; i<64; i++) {
  
		if (SDLNet_UDP_Recv(sd, p))
		{
			printf("UDP Packet incoming\n");
			printf("\tChan:    %d\n", p->channel);
			printf("\tData:    %s\n", (char *)p->data);
			printf("\tLen:     %d\n", p->len);
			printf("\tMaxlen:  %d\n", p->maxlen);
			printf("\tStatus:  %d\n", p->status);
			printf("\tAddress: %d %d\n", p->address.host, p->address.port);
			
			char *test[sizeof(strtok((char *)p->data, " "))];
			int dirValue;
			test[0] = strtok((char *)p->data, " ");
			int zxcv=getClientStick(p->address.host, p->address.port);
			if (strcmp(test[0], "stickman")==0 && zxcv!=-1) {
			  test[1] = strtok (NULL, " ");
			  test[2] = strtok (NULL, " ");
			  test[3] = strtok (NULL, " ");
			  dirValue=atoi(test[2]);
			  printf("So, what we see here is that dirValue=%d...\n",dirValue);
			  stickman[zxcv].direction=dirValue;
			  //stickman[atoi(test[1])].position.y=atoi(test[3]);
			  if (atoi(test[3])==1) { // Jump
			    if (stickman[zxcv].startJump()==true) {
			      Mix_PlayChannel(0,jumpsnd,0);
			    }
			  }
			}
			if (strcmp(test[0], "connect")==0) {
			  printf("CONNEXION\n");
			  clients.resize(clients.size()+1);
			  clients[clients.size()-1].client_ip=p->address.host;
			  clients[clients.size()-1].client_port=p->address.port;
			  clients[clients.size()-1].client_stick=addStickFigure();
			}
		}
}
  
}


int getStickFigures() {
  int theStickId, rint[20];
  for (int i=0; i<64; i++) {
		if (SDLNet_UDP_Recv(sd, p))
		{
			printf("UDP Packet incoming\n");
			printf("\tChan:    %d\n", p->channel);
			printf("\tData:    %s\n", (char *)p->data);
			printf("\tLen:     %d\n", p->len);
			printf("\tMaxlen:  %d\n", p->maxlen);
			printf("\tStatus:  %d\n", p->status);
			printf("\tAddress: %d %d\n", p->address.host, p->address.port);
			
			char *test[sizeof(strtok((char *)p->data, " "))];
			test[0] = strtok((char *)p->data, " ");
			if (strcmp(test[0], "stickman")==0) {
			  test[1] = strtok (NULL, " ");
			  test[2] = strtok (NULL, " ");
			  test[3] = strtok (NULL, " ");
			  test[4] = strtok (NULL, " "); rint[4]=atoi(test[4]);
			  test[5] = strtok (NULL, " "); rint[5]=atoi(test[5]);
			  test[6] = strtok (NULL, " "); rint[6]=atoi(test[6]);
			  test[7] = strtok (NULL, " "); rint[7]=atoi(test[7]);
			  test[8] = strtok (NULL, " "); rint[8]=atoi(test[8]);
			  test[9] = strtok (NULL, " "); rint[9]=atoi(test[9]);
			  test[10] = strtok (NULL, " "); rint[10]=atoi(test[10]);
			  test[11] = strtok (NULL, " "); rint[11]=atoi(test[11]);
			  test[12] = strtok (NULL, " "); rint[12]=atoi(test[12]);
			  test[13] = strtok (NULL, " "); rint[13]=atoi(test[13]);
			  test[14] = strtok (NULL, " "); rint[14]=atoi(test[14]);
			  test[15] = strtok (NULL, " "); rint[15]=atoi(test[15]);
			  test[16] = strtok (NULL, " "); rint[16]=atoi(test[16]);
			  test[17] = strtok (NULL, " "); rint[17]=atoi(test[17]);
			  test[18] = strtok (NULL, " "); rint[18]=atoi(test[18]);
			  test[19] = strtok (NULL, " "); rint[19]=atoi(test[19]);
			  
			  for (int i=4; i < 20; i++) {
			    printf("rint[%d]=%d",i,rint[i]);
			  }
			  
			  theStickId=atoi(test[1]);
			  stickman[atoi(test[1])].position.x=atoi(test[2]);
			  stickman[atoi(test[1])].position.y=atoi(test[3]);
			  std::cout << "Right before the input functions...\n";
			  stickman[theStickId].left_arm.setPoints( rint[4],rint[5],rint[6],rint[7] );
			  stickman[theStickId].right_arm.setPoints( rint[8],rint[9],rint[10],rint[11] );
			  stickman[theStickId].left_leg.setPoints( rint[12],rint[13],rint[14],rint[15] );
			  stickman[theStickId].right_leg.setPoints( rint[16],rint[17],rint[18],rint[19] );
			  std::cout << "asdfasdfasdf\n";
			}
			std::cout << "lastpartofif\n";
		}
		std::cout << "beforeendofor\n";
	}
	std::cout << "absoluteendoffunction\n";
}



int sendStickFigures() {
  //p->data=(Uint8 *)"connect"
  int tempInt;
  std::string stickCoords;
  for (int j=0; j < clients.size(); j++) {
  for (int i=0; i < 255; i++) {
    tempInt=i;
    if (tempInt==0) tempInt=clients[j].client_stick;
    else if (tempInt==clients[j].client_stick) tempInt=0;
    if (stickman[i].exists==true) {
  forIntsUsually.str("");
  forIntsUsually << "stickman " << i << " " << stickman[i].position.x << " " << stickman[i].position.y
    << " " << stickman[i].left_arm.output() << " " << stickman[i].right_arm.output() << " " << stickman[i].left_leg.output() << " " << stickman[i].right_leg.output();
		p->data=(Uint8 *)forIntsUsually.str().c_str();
		p->address.host = clients[j].client_ip;	/* Set the destination host */
		p->address.port = clients[j].client_port;	/* And destination port */
 
		p->len = strlen((char *)p->data) + 1;
		SDLNet_UDP_Send(sd, -1, p); /* This sets the p->channel */
    }
  }
  }
}


int sendStickFigure() {
  //p->data=(Uint8 *)"connect"
  //std::string stickstuff;
  //int asdf=(stickman[current].direction==-1) ? 2 : stickman[current].direction;
  int asdf=stickman[current].direction;
    forIntsUsually.str("");
    forIntsUsually << "stickman " << current << " " << asdf << " " << keyPressed;
		p->data=(Uint8 *)forIntsUsually.str().c_str();
		p->address.host = srvadd.host;	/* Set the destination host */
		p->address.port = srvadd.port;	/* And destination port */
 
		p->len = strlen((char *)p->data) + 1;
		SDLNet_UDP_Send(sd, -1, p); /* This sets the p->channel */
}

void doNetworkStuff() {
  if (is_server==true) {
    getPackets();
    sendStickFigures();
  }
   if (is_client==true) { 
    sendStickFigure();
    printf("getStickFigures();\n");
    getStickFigures();
    printf("after getStickFigures();\n");
  }
}

```

---

### Post by nathan.the.sane on 2012-04-09
Alright, here's something that looked strange.

In this line:

char *test[sizeof(strtok((char *)p->data, " "))];

it looks like you're declaring an array of char pointers. Isn't sizeof(strtok((char *)p->data, " "))
always going to be the same as sizeof(char*), i.e. 8 (or 4, depending on whether you're
on 64 or 32 bit)? Yet you're writing to test[19] and stuff. I think that is a problem, if not THE problem.

---

### Post by compiz addict on 2012-04-09
> **nathan.the.sane said:**
> Alright, here's something that looked strange.

In this line:

char *test[sizeof(strtok((char *)p->data, " "))];

it looks like you're declaring an array of char pointers. Isn't sizeof(strtok((char *)p->data, " "))
always going to be the same as sizeof(char*), i.e. 8 (or 4, depending on whether you're
on 64 or 32 bit)? Yet you're writing to test[19] and stuff. I think that is a problem, if not THE problem.

p->data is a Uint8*, and that is supposed to measure the size of it... I think I took that part right off of my reference for UDP networking in SDL_net. I changed it to "char *test[20];", but same problem.

---

### Post by Some Penguin on 2012-04-09
Things that come to mind:

1) You're mixing C/printf and C++/stdout.  This is generally a very bad idea.  Stick with one or the other.

2) You're using strtok; not strtok_r.  strtok is not threadsafe.

3) strtok is free to mutate the char* it receives.  This is potentially a problem when the string you've passed belongs to the strings table of your binary, e.g. 
  p->data=(Uint8 *)"connect";
does not allocate space for a copy of that char*, but only uses the shared one.

4) You're not showing how the stickman array was initialized.

---

### Post by compiz addict on 2012-04-10
> **Some Penguin said:**
> Things that come to mind:

1) You're mixing C/printf and C++/stdout.  This is generally a very bad idea.  Stick with one or the other.

2) You're using strtok; not strtok_r.  strtok is not threadsafe.

3) strtok is free to mutate the char* it receives.  This is potentially a problem when the string you've passed belongs to the strings table of your binary, e.g. 
  p->data=(Uint8 *)"connect";
does not allocate space for a copy of that char*, but only uses the shared one.

4) You're not showing how the stickman array was initialized.

Thanks for the response! So, I'm guessing the reason why mixing printf and stdout is bad is for debugging reasons, and they act a little differently while accomplishing the same thing. Am I right? I'm a little new to C++, so please forgive any ignorance.

The strtok isn't in a thread, but I'm guessing SDL_net is threaded - does this matter if the function is not used within a thread?

As for your 3rd point, I'm not 100% sure what you're trying to tell me. I believe that wouldn't effect it because SDLNet_UDP_Recv probably re-sizes it, though I should probably get more familiar with the library.

The stickman array is an array of 255 of the following class:

```

class stickFigure {
public:
SDL_Surface *surface;
SDL_Rect position;
complexMath tehmaths;
std::string name;
Uint32 lastShoot;
int direction;
int jumping;
float jumpFactor;
int health;
int jumpbar;
bool exists;
bool jumpPending;
aLine left_arm, right_arm, left_leg, right_leg;
aLine l_left_arm, l_right_arm, l_left_leg, l_right_leg;
int ai;
int leg;
int limbAngle[5][2];
int directAngle[5][3];
void reset();
void reposition();
void update(Uint32 pixel);
void bendLimb(int limb, float angle1, float angle2);
void move(int xd, int yd);
void walk(int dt);
void jump(int dt);
void mouseArms(SDL_Surface *surface,Uint32 pixel,int,int);
int physics();
bool startJump();
};

```

---

### Post by compiz addict on 2012-04-11
Well, I just made another UDPpacket for that function called p2 and it works, so you must be right. Now I just need to fix it so it handles errors on strtok, seeing as at the moment the server after about 3 times sends a packet with nothing in p->data (or at least not valid string with (char *)p2->data). Still not sure why it does that, but I might as well fix it this way to hacked clients can't segfault the server (that would be pretty bad, lol)

---

### Post by Some Penguin on 2012-04-12
> **compiz addict said:**
> Thanks for the response! So, I'm guessing the reason why mixing printf and stdout is bad is for debugging reasons, and they act a little differently while accomplishing the same thing. Am I right? I'm a little new to C++, so please forgive any ignorance.


In particular, I'd worry about them buffering output inconsistently.  An output stream doesn't necessarily flush everything every call, and if the two hit different buffers for some reason then you might get things out of order.

> 
The strtok isn't in a thread, but I'm guessing SDL_net is threaded - does this matter if the function is not used within a thread?


That's fine, then.

> 
As for your 3rd point, I'm not 100% sure what you're trying to tell me. I believe that wouldn't effect it because SDLNet_UDP_Recv probably re-sizes it, though I should probably get more familiar with the library.


Basically, when you do something like

  char* blah = "foo";

that 'foo' will be four bytes (counting the terminating null) somewhere in the processes' data space.  'blah' will be given that memory address -- it doesn't get a new copy.

Now, if you create multiple packets and initialize them so that their pointers all point to that bit of memory, that can work... if nobody changes the contents.  strtok(), however, is free to change the contents, and that causes trouble.

See [http://stackoverflow.com/questions/349025/is-a-string-literal-in-c-created-in-static-memory]("http://stackoverflow.com/questions/349025/is-a-string-literal-in-c-created-in-static-memory") for instance.

---

