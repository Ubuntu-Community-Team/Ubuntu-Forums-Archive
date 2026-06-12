---
title: "Network Programing - SDL_net"
date: 2011-07-02
forum: Programming Talk
---

### Post by Cpt_USMC on 2011-07-02
Hello, 
Ok, so I’ve made a few games before but never messed with servers/clients and all that fun stuff.  I’m not creating anything too crazy, so in order to get my feet wet I’m messing with SDL_net.  Now, SDL_net definitely has totally awesome documentation but for a person like myself, who programs as a hobby, never took a class and only learned how to do this stuff from forums and references, most of this material is going over my head.  So I was wondering if you could help me get my head above the water (By the way I am mainly working from a UDP approach, even though my games aren’t that demanding, as I progress I figure I will require this).      

For Example:      
*SDLNet_ResolveHost( IPaddress * address, char * host, Uint16 port )*      
Ok, assuming this is a client, than “host” is the name of the server the client is connecting to?  I know when connecting to yourself you can use “localhost” but outside of that, I have no idea.  I mean would I just enter the server’s IPaddress or is it way more confusing and complicated…lol?  And the “port” is the server’s port? And when it’s done, presuming no errors, it will fill the IPaddress’s pointer with the Server’s IP address & port it is listening on?  Than with setting a package by, p->address.host = address.host; and p->address.host = address.port; you are setting the package’s destination to the server right?  So when the server receives this packet do these variables now hold the client’s information?  I mean, how does the server know where this came from so it can send something back?   
Ok on the flip side…       
If this is relating to the server you set the “host” to NULL and it creates a server type IPaddress on the specified port.  What does that mean?  I found some documentation saying something about listening for activity, but is it listening for activity only on that specified port?  Does it allocate a completely different port to listen for this activity?  Does that port receive the packets from the client?  What if there are multiple clients?  Is the IPaddress pointer holding the server’s address?  OMG, I just rapped fired questions…sorry.  But I really don’t understand what it means or why it is used or when it is applicable to be used?  And if it is listing for activity wouldn’t a SDLNet_SocketSet be more useful or at least give you the ability to do the same thing through SDLNet_CheckSocket and SDLNet_SocketReady?      

Another Example:       
*SDLNet_UDP_Bind( UDPsocket sock, int channel, IPaddress * address )*       
What is this for?  Does it just increase the speed of the server sending stuff to a client; by the way I am presuming that the socket is pertaining to a client, and that the address is the clients IP, but idk?      

Another Example:       
*SDLNet_UDP_GetPeerAddress( UDPsocket sock, int channel )*      
Would this be what the server would use to get the IPaddress of a client trying to connect?  Again, I don’t know what that is used for either or when it is applicable?  Sorry that this is so long but when I finally get stuck and need to consult the forums I usually bring a list…lol.    

Thanks you for your time,  
~Cpt_USMC

---

