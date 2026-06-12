---
title: "Howto: config PuTTY to conect to your ubuntu"
date: 2008-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by segalion on 2008-09-02
Howto config putty to conect to ubuntu.
[IMG]https://sites.google.com/site/puttyandsshtunneling/_/rsrc/1277217498810/home/putty%20tunneling.gif[/IMG]
Finally I have found a fine configuration in ssh/telnet client PuTTY ( [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) ) to conect to default ubuntu sshd conections, with the text code character set for linedrawing.

This let you to conect to console to your ubuntu machine from i.e other windows remote PCs, and use programs like:
- text web browser: elinks
- text IM client (pidgin): flinch
- text Music player: ncmpc

Thats waht you have to put at your PuTTY config:
Window>Translation: 
	- Character set translation on received data = UTF-8
	- Adjust how to PuTTY handles line drawing character = Use Unicode line drawing code points
Connection:
	- Sending of null packets to keep session active = 60 # to avoid disconection from server because inactivity
Connection>Data
	- Terminal Details - Terminal-type string = linux
The other parameter seemps to work fine by default.

If you want to connect to your linux box via ssh (secure shell), you need to have installed and running ssh package (openssh-client and openssh-server) :
$sudo apt-get install ssh

you can edit your /etc/ssh/sshd_config with the "Port" where ssh server listen (defaul 22, but you can use 443 to cross firewall and proxy...)

With PuTTY and ssh conection, you can use a poweful feature:
make tunnels between your PuTTY (local computer) and your remote ubuntu box, in order to run programs as you where at your ubuntu.
I.e, if you are running mlnet ( [http://mldonkey.sourceforge.net/Main_Page](http://mldonkey.sourceforge.net/Main_Page) ) configured with the default local webserver [http://admin@127.0.0.1:4080](http://admin@127.0.0.1:4080)

You could configure PuTTY:
Connection>SSH>Tunnels: 
	- Source port=4080 
	- Destination=127.0.0.1:4080
	- Local and Auto enabled and Add button to add the tunnel

Then, if you open the ssh PuTTY connection an then run a local webbrowser at [http://admin@127.0.0.1:4080](http://admin@127.0.0.1:4080), you will see the web interface of the mlnet at ubuntu.

You can make as tunnels as applications you want to use(freevo, mpd webclient, etc), or even if you install a webproxy server at your ubuntu box, you could use this tunnel to navigate at your PuTTY PC as if you were at your ubuntu box.

There are more interesting links:

Putty for symbian, to control your linux from your mobile everywhere...
[http://s2putty.sourceforge.net/](http://s2putty.sourceforge.net/)

Portable putty version to not depend on windows registry:
[http://jakub.kotrla.net/putty/](http://jakub.kotrla.net/putty/)

At this you can try plink that is a commandline putty to make tunneling, and very good for scripting in windows...

A opensource Xserver implementation for windows... [http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)



> [QUOTE][/QUOTE]

---

