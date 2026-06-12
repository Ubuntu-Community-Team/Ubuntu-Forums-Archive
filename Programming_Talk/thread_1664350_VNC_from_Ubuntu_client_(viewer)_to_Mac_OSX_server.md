---
title: "VNC: from Ubuntu client (viewer) to Mac OSX server"
date: 2011-01-10
forum: Programming Talk
---

### Post by sdaau on 2011-01-10
Hi all, 

Every once in a while I have to assist remotely a Mac OSX user; and every time I spend the better portion of the day hacking my way through to the OSX desktop (instead of assisting). So I thought this time I'd write it up. The situation is shown below (drawn with [JavE](http://www.jave.de/download/download.html); also note that 91.189.94.156 and 17.251.200.70 are public IPs of ubuntu.com and apple.com respectively; whatever I got back first from ping). 

```

                                                                              ________________________
    _______________________                                                   |                      |
   |                      |                                          ,________|_______  Mac OSX user |
   |  Ubuntu user ,_______|________       ,---..-',---._             |               |               |
   |              |               |      '.             `--._________| Public IP:    |   VNC server `:----
   | o VNC client | Public IP:    |_____/:-   Internet    ,-'        | 17.251.200.70 |               |\\\
   |dP            | 91.189.94.156 |    `,'                |          |_______________|   ssh client  | \8'
   dP  ssh server |_______________|      `'''\_____ ____.-'                   |_____________,=,d8ooooo8P'
  J8i________._-./..______|                                                            _,-',o8P'''
  `8o____,oooo.i.\``-.._                                                           _.-' _o8P'
    `"""""''``"P8oo._   `'--...__                                            _,.-''  ,o8P'
                  `"P8oo._       ``--...___      (ssh tunnel)       _,,..---'    _oo8P'
                       '"YPYbooo.__        `'-------.......,-----'''       __oodPP''
                              ''""PP8ooooo____                    __,oooo8PP"''
                                      `''`"""YPPPPP8oooooooooo8PPPP""''
									  

```

To restate - I'm in the role of Ubuntu user, and I'd like to remotely assist a Mac OSX user, by taking over the desktop temporarily. There are usually some problems with this: 
[list]
[*] *Mac user is usually behind a firewall*. 
[*] *Mac OSX does **NOT** like you to use 'localhost'; use 127.0.0.1 **ALWAYS**. *. 
[*] *Mac OSX doesn't really have a VNC server - use [Vine Server (OSXvnc)](http://sourceforge.net/projects/osxvnc/files/Vine%20Server%28OSXvnc%29/)*. 
[*] Once you have a VNC connection to the Mac OSX desktop via Vine Server, **NEVER** press 'Insert' or 'CTRL' keys in the [FONT="Courier New"]vncviewer[/FONT]!
[/list]

For the firewall problem: while sometimes I have to go through exchanging screenshots and such via chat, until their firewall starts allowing VNC connections - its usually easier to implement a '[Reverse Shell](http://www.plenz.com/reverseshell)': ask the Mac User to tunnel their VNC port to me via ssh -- as I'm usually in a position to both take my own firewall down, and run a ssh server as well; and Mac OSX also has an ssh client installed by default. Then, I can initiate a client connection to the locally tunneled port without a problem.  
[list]
[*] Note also, that often for VNC via SSH on Mac OSX, you can find recommendations like "* In System Preferences in Sharing, turn on 'Remote Login', which is SSH.*" ( [Remote Management vs. Screensharing vs. VNC on OS X - vnc osx leopard](http://ask.metafilter.com/101910/Remote-Management-vs-Screensharing-vs-VNC-on-OS-X)) -- however, if the reverse shell technique is used, it should not be necesarry (*since in reverse shell, the Mac user will have the role of ssh client; not ssh server*). 
[/list]

However, you may *still* experience problems like described in [SSH port forwarding since 10.3 [Archive] - The macosxhints Forums](http://hintsforums.macworld.com/archive/index.php/t-22524.html):
> **"http://hintsforums.macworld.com/archive/index.php/t-22524.html"]
>> With 10.2, I could, without modifying my sshd config files, ssh 
>> into my computer and tunnel VNC through it. ...
>> However, since upgrading to 10.3, attempting to run the vnc 
>> client gives an error in my ssh session:
>> channel 2: open failed: connect failed: Connection refused
>> 
---
> 
> Try -L 5900:127.0.0.1:5900 instead of -L 5900:localhost:5900.
> 
> I had the same problem then I read this suggestion somewhere. 
> Apparently it is because OpenSSH is (now?) IPv6 aware, so you 
> need to explicitly use an IPv4 address or it might get confused.
> 
---
Once I used 127.0.0.1 instead of "localhost" I was able to make
the connection without problems
[/quote]


The third problem is more tricky, because the first thing I do there, is of course, type a search like 'Mac OSX VNC server' said:**
> How to Setup VNC on Mac OS X - wikiHow[/url], which claim:
[quote="http://www.wikihow.com/Setup-VNC-on-Mac-OS-X"]
Need to control an Apple computer running OS X 10.4 Tiger or OS X 10.5 Leopard from a remote location? That's the purpose of VNC! 
...
OS X 10.4 and 10.5 include the server component out of the box so all we need to do is turn it on.
1
Open your System Preferences from your blue apple menu.
...
4
Click Start to fire up Apple Remote Desktop service.


... which is, of course, a load of bullcrap :) 

... because as soon as you've established your tunnel; and you try to connect using, say, [FONT="Courier New"]vncviewer[/FONT] or [FONT="Courier New"]xvnc4viewer[/FONT] -- you get the surprise of actually passing VNC password authentication at first; and then the VNC screen (if it appears) dying/crashing/quitting **immediately** (also noted in [RealVNC quits on connect...](http://www.realvnc.com/pipermail/vnc-list/2007-January/056769.html)). Meanwhile, the trusty VNC client log will inform us: 

```

 CConn:       connected to host XXX.XXX.XXX.XXX port 5900
 CConnection: reading protocol version
 CConnection: Server supports RFB protocol version 3.889
 CConnection: Using RFB protocol version 3.8
 CConnection: processing security types message
 CConnection: Server offers security type [unknown secType](30)
 CConnection: Server offers security type VncAuth(2)
 CConnection: Choosing security type VncAuth(2)
 CConnection: processing security message
 CConnection: processing security result message
 CConnection: processing security result message
 CConnection: Authentication success!				<==== !!! 
 CConnection: reading server initialisation
 CConnection: initialisation done
 TXImage:     Using shared memory XImage
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding
 DesktopWindow: selection (1) time is 278389, later 1
 TXImage:     Freeing shared memory XImage			<=== here it dies, instantly
 main:        End of stream

```

... that is: no errors, except that window silently dissapears ?! 

Well, so, the truth is really that "*Apple Remote Desktop isn't VNC compatible*" ([vncviewer not working with Mac OS X VNC Server](http://www.realvnc.com/pipermail/vnc-list/2007-January/056874.html)):
[quote="http://www.realvnc.com/pipermail/vnc-list/2007-January/056874.html"]
Apple Remote Desktop isn't VNC compatible, as you can see from the log
output below, in which the server reports a bogus protocol version.  VNC
Enterprise & Personal Editions have a workaround for server software that is
broken in this way, and that will be in the next Free Edition release, too.

You can get VNC Server Enterprise Edition for Mac OS X from
[http://www.realvnc.com/download.html](http://www.realvnc.com/download.html), and there are also some projects based
on our Free Edition codebase, such as OSXvnc, which provide VNC servers for
Mac OS X.
[/quote]

Hmm.. I don't really see how I can "*see from the log output*" that "*Apple Remote Desktop isn't VNC compatible*"; as there are no error messages :( But nevermind - at least we have it in writing now :) 


Thankfully, someone else has apparently been irritated by this too -- having produced the software that saves the day in this case: [Vine Server (OSXvnc)](http://sourceforge.net/projects/osxvnc/files/Vine%20Server%28OSXvnc%29/). 

So you ask the Mac user to shut down Apple Remote services, and install and run Vine server instead - and things can finally start rolling. The problem is, once connection is established, one can still stumble into [How to prevent question mark cursor issue cause be Insert key when doing VNC to a mac?](http://superuser.com/questions/94326/how-to-prevent-question-mark-cursor-issue-cause-be-insert-key-when-doing-vnc-to-a): i.e., if you press Insert (for me also Ctrl) in the VNC viewer on Ubuntu - that sends something strange to Vine server, which then afterwards stops responding to keyboard keystrokes, and the cursor turns into a question mark; at this point, the Max user is usually forced to reboot. 


Well, after this discussion, here is then what (I hope) is the right sequence of events (IP addresses are in respect to above diagram): 

[list]

[*] Mac user does: 
[list]
[*] Disable Apple Remote, and then run Vine server
[*] Wait until Vine server shows a port number (could be 5900 or 5901, and can apparently change sometimes; lets say it shows 5901)
[*] Establishes ssh tunnel to the Ubuntu user's ssh server, using: ```
ssh -NR 3333:127.0.0.1:5901 GUESTUSER@91.189.94.156
```
[/list]

[*] Ubuntu user now does: 
[list]
[*] Establish ssh tunnel from server's 3333 to local port 5902, using ```
ssh -NL 5902:127.0.0.1:3333 myUser@myLocalSSHServer
``` (where 'myLocalSSHServer' could be either 127.0.0.1 if ssh server is running on same ubuntu PC, or 192.168.X.X if it's running elsewhere on local network)
[*] Call vncviewer/xvnc4viewer to connect to the locally forwarded port, 5902: ```
xvnc4viewer -LowColourLevel 2 -AutoSelect=0 -geometry 800x600+0+0 127.0.0.1::5902
```
[*] Once connected, avoid pressing 'insert' or 'Ctrl' in [FONT="Courier New"]xvnc4viewer[/FONT] (ask Mac user for assistance if needed; or say if using nano, use 'Esc' then 'r' to run Search/Replace - instead of the usual Ctrl-R or Alt-R (gnome will eat the 'Alt' here))
[/list]

[/list]

I believe that should be correct command line above for [FONT="Courier New"]xvnc4viewer[/FONT] to establish connection to port 5902; if it doesn't work -- then simply ensure first that the local Gnome 'Remote Desktop' is turned off on the vnc client Ubuntu machine (as it will otherwise conflict, running on port 5900); then establish ssh tunnel to local port 5900 (instead of 5902 as above); and finally just call xvnc4viewer without the port argument '::5902' at end (that is, just use [FONT="Courier New"]xvnc4viewer -LowColourLevel 2 -AutoSelect=0 -geometry 800x600+0+0 127.0.0.1[/FONT]). 

Well, hope that was it - and next time, I won't have to use an entire day on this :) 

Cheers!

---

