---
title: "HowTo: SSH Tunnel Firefox"
date: 2008-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by wormser on 2008-03-13
A ssh tunnel for Firefox to a remote computer is good security measure.  Especially when connecting via an untrusted network like a wifi hotspot or other public networks.  The tunnel encrypts and sends the data to your remote machine then it is sent over the web to your destination.  This tutorial assumes you have an account on a remote machine you can ssh into.  This is a pretty easy set up.

The command to connect

```
ssh -D 9999 -C me@ipaddress.com
```

The -D switch - Specifies a local &#8220;dynamic&#8221; application-level port forwarding.  We are also adding the -C switch for compression.

Next we need to put the settings into Firefox.  

Firefox> Edit> Preferences> Advanced tab> Network tab> Settings button.

Select Manual proxy configuration
SOCKS Host: localhost    Port: 9999
SOCKS v5
No Proxy for: localhost, 127.0.0.1
*Screenshot below.*

*Note: Sometimes localhost can cause a problem.  If your settings are right and it still is not working replace localhost with 127.0.0.1.*


Using the ssh SOCKS5 proxy all of your info is passed through the tunnel except DNS requests. DNS requests are requests that look up names like google.com and turn them into IP addresses. If you want your DNS requests to go through the SOCKS5 proxy (yes you want this feature -- trust me if you are going through all the trouble to create this encrypted tunnel), you need to do the following.

1. Open up firefox
2. Type about:config on the location bar
3. Filter for the following: network.proxy.socks_remote_dns
4. Set the value to True (Right Click on the value in the column)
5. Restart Firefox

Now all DNS requests will go through the SOCKS5 proxy rather than the local network.

Thanks to Kevdog for the DNS section.

---

### Post by wieman01 on 2008-03-13
Nice one. Thank you. I will certainly use it.

---

### Post by kevdog on 2008-03-13
Not a bad tutorial, but if you could expand it to include the server setup (for beginners) it would be very helpful.  Also probably would be preferrable to run ssh over a different port, however that's just a concern of mine.

---

### Post by wieman01 on 2008-03-13
You have a point, Kevdog, public providers might block certain ports.

---

### Post by vik.vaughn on 2008-03-21
Is there was a way to do this without having putty open and running? (Windows)

---

### Post by spotdart on 2008-03-21
is there a way to test if the tunnel is working?

---

### Post by kevdog on 2008-03-21
Vik

In windows you need to establish the ssh connection to the server.  I know there are several ways of doing this -- however putty is one of the most popular clients. There are others however.  I'm not certain but I dont think the foxy proxy plugin for firefox has the ability to first log into the ssh server and then establish the proxy.  You may want to check into this.  None the less, you need a client to make a connection first

spotdart

The best way I know to verify you are connected to the proxy is while uisng the proxy, at your browser use:

[http://showmyip.com](http://showmyip.com)

What should be shown here is the IP address of the proxy server rather than your physical IP address.  Try visiting the site with and without the proxy and the IP address should be different.

---

### Post by vik.vaughn on 2008-03-22
I just checked out foxyproxy, it doesn't have the ability to automatically login to SSH, but it is a very robust proxy tool. I'll definitely be using that from now on.

I'm going to shoot an email to the foxy proxy folks and request that they add SSH functionality since it seems like a very popular way to securely proxy.

---

### Post by kevdog on 2008-03-22
vik

I think that sounds like a great idea -- I think that would be a welcome addition to that useful proxy add-on.

---

### Post by kevdog on 2008-03-22
Hey just wanted to add some info to your SOCKS5 proxy tunnel setup. 

Using the ssh SOCKS5 proxy all of your info is passed through the tunnel except DNS requests.  DNS requests are requests that look up names like google.com and turn them into IP addresses.   If you want your DNS requests to go through the SOCKS5 proxy (yes you want this feature -- trust me if you are going through all the trouble to create this encrypted tunnel), you need to do the following.

1. Open up firefox
2. Type about:config on the location bar
3. Filter for the following: network.proxy.socks_remote_dns
4. Set the value to True (Right Click on the value in the column)
5. Restart Firefox

Now all DNS requests will go through the SOCKS5 proxy rather than the local network.

---

### Post by vik.vaughn on 2008-03-23
I made the suggestion on the FoxyProxy forum [here]("http://z9.invisionfree.com/foxyproxy/index.php?showtopic=662&st=0&#entry11789655")

---

### Post by Régis B. on 2008-03-29
God! Thank you a thousand times Wormser! I knew this thing existed but I just didn't know the ssh switch. MOUAHAHA now I can check Wikipedia, read the news, install freenet and say a big "allez vous faire foutre" to all the censors.

(I live in China)

Life rocks!

---

### Post by dschaller on 2008-04-02
I too have been wanting to know how to do this. I'm anxious to try it now. Do I have to change any settings on my router to allow this?

---

### Post by kevdog on 2008-04-02
Yes on the router you need to port forward the ssh port to the server.  Most ssh servers listen on port 22 by default, so if you are sticking with the default configuation you would port forward port 22 from the router to the IP address of the ssh server.  

I would highly recommend however you change your sshd_config file to run ssh on another port -- not port 22.  Port 22 is often scanned by script kiddies and other nefarious network scanning tools on the web.  If you run your ssh daemon on another port, say port 2222, then in order to connect it would be:

ssh -D 9999 -p 2222 -C [email]me@ipaddress.com[/email]

---

### Post by dschaller on 2008-04-03
Thank you. I will definitely try this the next time I am away from home.

---

### Post by se2131 on 2008-04-30
If you have multiple programs with which you would like to use an SSH tunnel with, a better option may be to System > Preferences > Network Proxy. Very similar setup as with the firefox dialog

Check Manual Proxy configuration
Socks host : localhost: *port*
Close

Then in Firefox, just check off the "Use system proxy settings" option in the dialog where you configured the proxy before.

This way, if you want to use Pidgin or IRC or whatever with the SSH tunnel, you don't need to re-configure them everytime you use a public wifi router. You can just toggle between "Direct Internet connection" and "Manual proxy configuration" from the System > Preferences > Network Proxy dialog. Of course this only works if those programs have a "use system settings" option, I know that Pidgin does this automatically at least.

---

### Post by se2131 on 2008-04-30
For those ppl trying to figure out how to get this to work with Opera (which doesn't support SOCKS natively for some reason), look to this:

[http://www.plenz.com/tunnel-everything](http://www.plenz.com/tunnel-everything)

Here are the steps based off of that article

1) sudo aptitude install tsocks (you may already have this)

2) sudo nano /etc/tsocks.conf

3) Comment out everything in that file

4) At the end of the file, add these two lines:

```
server = 127.0.0.1
server_port = 9999
```

5) Save and close

6) Start your SSH session: ssh -D 9999 user@server

7) run "tsocks opera"

The great thing about tsocks is that you can run a lot of programs through it (maybe all? dunno).

---

### Post by knottshawk on 2008-05-16
I've always used ssh on windows and mac, but I can't get this to work on my xubuntu machine. I can connect via putty, but firefox won't recognize what I'm doing.

I can get it to work from my terminal...just not from putty. The terminal would be fine except that I don't want to jump into the terminal and type ssh -D 1088 -p 80 [email]username@ipaddress.com[/email] every time I want to get online.

Is there a quicker way? (I'm a linux noob)

---

### Post by se2131 on 2008-06-07
> **knottshawk said:**
> I've always used ssh on windows and mac, but I can't get this to work on my xubuntu machine. I can connect via putty, but firefox won't recognize what I'm doing.

I can get it to work from my terminal...just not from putty. The terminal would be fine except that I don't want to jump into the terminal and type ssh -D 1088 -p 80 [email]username@ipaddress.com[/email] every time I want to get online.

Is there a quicker way? (I'm a linux noob)

I realize you posted this a while ago, but couldn't you make a bash alias? Uncomment these lines from .bashrc:

```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

Then edit your .bash_aliases file, and add an entry like this:

```

alias commandname = 'ssh -D 1088 -p 80 username@ipaddress.com'

```

Then all you would have to do is open a terminal and type in 'commandname'. Same amount of effort as opening a putty session and connecting that way

---

### Post by Darrena on 2008-06-07
Just a note, there is a great app in the Repo's to do this from a GUI call gSTM (Gnome SSH Tunnel Manager).

---

### Post by dalesd on 2008-07-05
Lots of good ideas here, but I'm a bit confused.  Here's what I want to do.

I'm running Hardy on my home PC, which is on 24/7.  I want this computer to act as my secure proxy so I can keep my traffic private while at work (Windows XP PC) or on the road with my wife's laptop (also Windows).

What goes on my Ubuntu PC to make this happen?  Also, how do I keep track of my IP address, which is dynamic and can change without warning?

---

### Post by kevdog on 2008-07-05
The only thing that needs to go on the server is the ssh daemon or server program.  If your home IP address keeps changing, sign up for an account with noip.com or dyndns.com (others too), that assign you a free domain name that will be assigned to your IP address.  Using their updater client, your ip address will be sent to their dns servers every 30 minutes and every boot to update your current ip address with your name.  This way you never need to know your ip address.  (noip.com has always worked well for me!!).  

On the client machine all you need is an ssh client.  The rest of the changes are made in firefox, although I recommend the foxy proxy extension, since this tends to make the configuration within firefox easy.

---

### Post by Truefire on 2008-09-13
I need to connect to the internet on my NetBook via a radically insecure college net. I setup freeSHHd on my home Vista box(I know!! it just won't work with Linux with the current crappy harddrive!)
and forwarded the port 27 to outside port 27,
and ran

 sudo ssh -D 9999 -p 27 -C rael@70.101.64.27

on the NetBook,
but it doesn't seem to work.

I set Firefox up the way the how to listed. What am I doing wrong?

PS: I'm _not_ a linux noob. CLI's are my friend.

---

### Post by Truefire on 2008-09-13
> **Truefire said:**
> 
and forwarded the port 27 to outside port 27,



EDIT: by this, I mean virtual server settings on the router.

---

### Post by Truefire on 2008-09-13
Ok, I got it working when I use 192.. when on a local network. Before, even when on a local, but trying to connect to outside IP, it didn't work, but maybe that's because I was on the same Network. 
I'll figure that part out, I guess, by myself.
---->
 Now, my new problem.
When I open firefox, the SSH session closes with the error:

buffer_get_ret: trying to get more bytes 4 than in buffer 0
buffer_get_int: buffer error

Is this a setting on the server, only allowing a certain number of bytes?
Or is it the client's issue? Can anyone give me a clue?

---

### Post by szr4321 on 2009-02-14
> **Truefire said:**
> Now, my new problem.
When I open firefox, the SSH session closes with the error:

buffer_get_ret: trying to get more bytes 4 than in buffer 0
buffer_get_int: buffer error

Maybe it's the same problem as described [here]("http://lglinux.blogspot.com/2009/02/ssh-connect-error.html")?

---

### Post by kevdog on 2009-02-14
I don't use dsa keys -- only rsa.  Maybe try generating only rsa keys.

---

### Post by excbuntu on 2009-03-07
how can i do this with dd-wrt running as the ssh server? would it use the same commands as described in the op? since my router is on all the time, i'd rather use that than having to wake up my power hungry pc.

---

### Post by kevdog on 2009-03-08
Within dd-wrt you need to turn on the ssh daemon.  This is located the Main Services Tab, and then under the subtab labeled services.

Scroll down and activate the ssh daemon under the Secure Shell section.  Select the appropriate options, particularly the SSH TCP forwarding option.  Just remember if you choose to use a password, the username is always going to be root.

---

### Post by Yourname on 2009-05-06
> **Darrena said:**
> Just a note, there is a great app in the Repo's to do this from a GUI call gSTM (Gnome SSH Tunnel Manager).

Thank you very much for pointing this out! Now if only I can make it start AFTER Network Manager is done setting up a connection ;)

---

### Post by TheSqueak on 2009-10-29
A word of warning for anyone using the "FoxyProxy" extension in Firefox to manage their proxies - regardless of whether you set the selection box to do so or not, FoxyProxy **will not** tunnel DNS requests - they will still be sent out in the clear

---

### Post by kevdog on 2009-10-29
The Squeak -- Then what is the best way around this?

---

### Post by TheSqueak on 2009-10-29
> **kevdog said:**
> The Squeak -- Then what is the best way around this?

I decided that I didn't really need that proxy extension, and i've uninstalled it. You could look at SwitchProxy instead, but I don't know for sure whether that one will do the same or not

---

### Post by SpzToid on 2010-01-10
> **TheSqueak said:**
> A word of warning for anyone using the "FoxyProxy" extension in Firefox to manage their proxies - regardless of whether you set the selection box to do so or not, FoxyProxy **will not** tunnel DNS requests - they will still be sent out in the clear

It _seems_ you can also tunnel DNS requests using FoxyProxy by editing the proxy, then clicking the proxy details tab, and checking ON the box that reads 'Use this proxy for all DNS lookups'.

But I haven't tested to see what get's sent into the clear. Still, it looks like the FoxyProxy developer's have taken dns requests into account.

---

### Post by ketetefid on 2011-01-28
Thank you very much for your nice tutorial. This guide makes it a breeze to bypass f_i_l_t_e_ring in restricted countries with dictatorial governments.
I just logged in to thank you.

---

