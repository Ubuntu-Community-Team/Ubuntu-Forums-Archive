---
title: "SDL_net Questions"
date: 2011-07-02
forum: Programming Talk
---

### Post by Cpt_USMC on 2011-07-02
I think you guys may have missed my post...:sad:...well basically I was wondering if you guys knew what these functions were, what they did, & when is it applicable for them to be used?  I'm using a UDP approach working from SDL_net.  Also, how does the server know where packets come from so it can send something back?         
[LIST]
[*]*SDLNet_ResolveHost( IPaddress * address, char * host, Uint16 port )*
[LIST]
[*]What does it mean when "host" is NULL?
[/LIST]
 
[*]*SDLNet_UDP_Bind( UDPsocket sock, int channel, IPaddress * address )*
[LIST]
[*]What are you binding and What is the purpose to binding?
[/LIST]
 
[*]*SDLNet_UDP_GetPeerAddress( UDPsocket sock, int channel )*
[LIST]
[*]When would you use this?
[/LIST]
 
[/LIST]
:KS PS: For a more detailed list of questions please visit my prior post.
[http://ubuntuforums.org/showthread.php?t=1795073](http://ubuntuforums.org/showthread.php?t=1795073)

Thanks,
~Cpt_USMC

---

### Post by bbqroast on 2011-11-25
> **Cpt_USMC said:**
>         
[LIST]
[*]*SDLNet_ResolveHost( IPaddress * address, char * host, Uint16 port )*
[LIST]
[*]What does it mean when "host" is NULL?
[/LIST]

You use NULL to tell it you are listening (a server listens).
> **Cpt_USMC said:**
>     
[*]*SDLNet_UDP_Bind( UDPsocket sock, int channel, IPaddress * address )*
[LIST]
[*]What are you binding and What is the purpose to binding?
[/LIST]

Binding is for sockets, it asks the OS "Oh, can I reserve port x?". In order to listen to a port you must bind it to your program.
> **Cpt_USMC said:**
> 
[*]*SDLNet_UDP_GetPeerAddress( UDPsocket sock, int channel )*
[LIST]
[*]When would you use this?
[/LIST]

To get the IP of the computer who sent you the packet.

---

