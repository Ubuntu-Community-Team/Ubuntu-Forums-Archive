---
title: "XChat is not looking up my hostname/registering me! What's going on?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-02
Hey all.

I was getting bored of my everyday system so I decided to install XChat. The installation was quick and smooth. However when I tried connecting to any server [ChatJunkies] it told me that it could not look up my hostname while registering me and started using my IP address. Within minutes, however I was disconnected yet again and it tried to re-connect within moments. Any bright ideas about what's happening guys:confused:

Armageddon

---

### Post by Joeb454 on 2008-06-02
Open up the Network List, and make sure you have a 2nd and 3rd choice for Nick's :)

---

### Post by spiderbatdad on 2008-06-02
[http://www.smogon.com/irc/xchat_tutorial](http://www.smogon.com/irc/xchat_tutorial)

You may also need to look at server specific documents. Register your nick.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-02
> **Joeb454 said:**
> Open up the Network List, and make sure you have a 2nd and 3rd choice for Nick's :)

Done tht.:(

---

### Post by Joeb454 on 2008-06-02
Are you still getting the error?

Can you post the output in here so we can see exactly what it says? Don't forget to use [code] tags ;) Makes it far easier to read :D

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-03
Here is what happens when I try to register my username - LeChomp on DejaToons

```
 Tcl plugin for XChat - Version 1.62 
 Copyright 2002-2005 Daniel P. Stasinski
 http://www.scriptkitties.com/tclplugin/
 Tcl interface loaded
 Perl interface loaded
 Python interface loaded
* Looking up irc.dejatoons.net
* Connecting to irc.dejatoons.net (63.243.153.239) port 7777...
* * Certification info:
*   Subject:
*     C=CA
*     O=Dejatoons
*     OU=IRCd
*   Issuer:
*     C=CA
*     O=Dejatoons
*     OU=IRCd
*   Public key algorithm: rsaEncryption (1024 bits)
*   Sign algorithm md5WithRSAEncryption
*   Valid since Oct 23 23:16:31 2006 GMT to Oct 23 23:16:31 2007 GMT
* * Cipher info:
*   Version: TLSv1/SSLv3, cipher AES256-SHA (256 bits)
* * Verify E: self signed certificate.? (18) -- Ignored
* Connected. Now logging in...
* *** Looking up your hostname...
* *** Checking ident...
* *** Couldn't resolve your hostname; using your IP address instead
* *** No ident response; username prefixed with ~
* USER :Not enough parameters
```

Any ideas what this means?

---

### Post by Joeb454 on 2008-06-03
Looks like you've not got something filled in, or characters in somewhere that the server doesn't like. I found [this page]("http://forum.xchat.org/viewtopic.php?t=730&sid=d0ea0c26d0b4e34c07ad9c17f0638ce6") Which basically says the same thing.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-03
nope, nothing like that at all. nickname is LeChimp. Don't think that the username is the problem. 


EDIT: woops!, I checked the USERNAME not the NICKNAME and turned out that was the problem!:oops:

Thanks a lot man!
Armageddon

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-03
:(
Although one problem was solved, another arose...

 ```
Copyright 2002-2005 Daniel P. Stasinski
 [http://www.scriptkitties.com/tclplugin/](http://www.scriptkitties.com/tclplugin/)
 Tcl interface loaded
 Perl interface loaded
 Python interface loaded
* Looking up irc.dejatoons.net
* Connecting to irc.dejatoons.net (208.98.8.66) port 6777...
* Stopped previous connection attempt (pid=12986)
* Looking up irc.dejatoons.net
* Connecting to irc.dejatoons.net (72.20.18.30) port 7777...
* * Certification info:
*   Subject:
*     C=US
*     ST=New York
*     O=Dejatoons
*     OU=IRCd
*   Issuer:
*     C=US
*     ST=New York
*     O=Dejatoons
*     OU=IRCd
*   Public key algorithm: rsaEncryption (1024 bits)
*   Sign algorithm md5WithRSAEncryption
*   Valid since Mar 10 17:32:52 2007 GMT to Mar  9 17:32:52 2008 GMT
* * Cipher info:
*   Version: TLSv1/SSLv3, cipher AES256-SHA (256 bits)
* * Verify E: self signed certificate.? (18) -- Ignored
* Connected. Now logging in...
* *** Looking up your hostname...
* *** Checking ident...
* *** Couldn't resolve your hostname; using your IP address instead
* *** No ident response; username prefixed with ~
* Welcome to the DejaToons IRC Network LeChimp!~LeChomp@121.246.234.18
* Your host is sebben.dejatoons.net, running version Unreal3.2.6
* This server was created Sat Mar 10 2007 at 09:33:20 PST
* sebben.dejatoons.net Unreal3.2.6 iowghraAsORTVSxNCWqBzvdHtGp lvhopsmntikrRcaqOALQbSeIKVfMCuzNTGj
* NAMESX SAFELIST HCN MAXCHANNELS=30 CHANLIMIT=#:30 MAXLIST=b:60,e:60,I:60 NICKLEN=30 CHANNELLEN=32 TOPICLEN=307 KICKLEN=307 AWAYLEN=307 MAXTARGETS=20 WALLCHOPS :are supported by this server
* WATCH=128 SILENCE=15 MODES=12 CHANTYPES=# PREFIX=(ohv)@%+ CHANMODES=beIqa,kfL,lj,psmntirRcOAQKVCuzNSMTG NETWORK=DejaToons CASEMAPPING=ascii EXTBAN=~,cqnr ELIST=MNUCT STATUSMSG=@%+ EXCEPTS INVEX :are supported by this server
* CMDS=KNOCK,MAP,DCCALLOW,USERIP :are supported by this server
* *** You are connected to sebben.dejatoons.net with SSLv3-AES256-SHA-256bits
* There are 50 users and 634 invisible on 10 servers
* 23 :operator(s) online
* 258 :channels formed
* I have 107 clients and 1 servers
* Current Local Users: 107  Max: 486
* Current Global Users: 684  Max: 2417
* - sebben.dejatoons.net Message of the Day - 
* - 7/6/2007 14:48
* - - ********************************************************
* - -
* - -           Welcome to the DejaToons Network
* - -
* - - All network servers are accessible via irc.dejatoons.net
* - -
* - -                                    
* - -          Website:  [http://www.dejatoons.net](http://www.dejatoons.net)
* - - 
* - -           Network help channel:  /join #help
* - -
* - - Network forum:  [http://forum.dejatoons.net](http://forum.dejatoons.net)
* - -
* - - ********************************************************
* - -
* - - Most ports between 6665-7002 are available.
* - - SSL is available on ports 6601 and 7777.
* - - 
* - - ********************************************************
* - -
* - - Network Rules:
* - -
* - - No Excessive Connections (Cloning).
* - - No Automated Downloading/Queing/XDCC Catching Scripts.
* - - No War Bots or War Scripts.
* - - No Bottler, Litmus, or IRC-ORK Clients.
* - - No Botnets.
* - - No Unauthorized XDCC bots - Join #help for more details.
* - - No Open proxies or BNC's.
* - - No Spamming, Mass Advertising or spreading Viruses/Trojans.
* - - No Nuking or DoS (Denial of Services) attacks.
* - - No Harrassment of fellow users.
* - - No Pornography.
* - - No Flooding.
* - - No Warez, XDCC, or Beta (illegal/copyrighted software/media) channels. 
* - - No Pre-release or Illegal movies, MP3's or Software.
* - -
* - -
* - - Any channel or user found breaking these rules (and who fail
* - - to take action to correct the situation) will be removed from
* - - the network.  If you feel you were unfairly terminated you may
* - - post a message at the network forum in the correct section.
* - - All complaints or logs presented MUST include timestamps.
* - -
* - - Upon connecting to this network, your system will be scanned
* - - for the presence of an insecure proxies and unwanted or
* - - infected clients and scripts.  Please do not view this as an
* - - attack.
* - -
* - - If you do not understand, disagree with this MOTD or disagree 
* - - with any of our network rules, please DISCONNECT NOW. 
* - - Otherwise, the following applies:
* - ---
* - --- You agree that you are a guest on a private system and use 
* - --- of this server and network is a priviledge, NOT a right.  
* - --- This privilege can be revoked at ANY time for ANY reason. 
* - --- Further you accept that you have no claim to any data 
* - --- maintained by Dejatoons that you have used.
* - ---
* - --- You also agree that by using Dejatoons, you may be exposed 
* - --- to offensive, indecent or objectionable content. Under no
* - --- circumstances will DejaToons be liable in any way for any 
* - --- content, including, but not limited to, for any errors or 
* - --- omissions in any content, or for any loss or damage of any 
* - --- kind incurred as a result of the use of any content posted, 
* - --- emailed, transmitted or otherwise made available via 
* - --- Dejatoons. 
* - ---
* - --- IRC is an unmoderated medium. You agree that you, and only
* - --- you are responsible for your own actions.  You also agree
* - --- that the network staff is NOT responsible for the content 
* - --- found on this network or server, except what is done through
* - --- their own actions.
* - -
* - - Bottom line...if you can exercise a little common sense and  
* - - follow the rules everything should be fine.
* - -
* End of /MOTD command.
* LeChimp sets mode +i LeChimp
* LeChimp sets mode +w LeChimp
* LeChimp sets mode +z LeChimp
* Received a CTCP VERSION from SecureServ
-NickServ- Your nick isn't registered.
* #smogon :You need a registered nick to join that channel.
```

When I try to register my nickname with LeChimp/ns register <my password for XChat> [email]snowbori_number_1@yahoo.com[/email] it gives me this:

```
* #smogon :You need a registered nick to join that channel.
 No channel joined. Try /join #<channel>
```

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-05
Bump

---

### Post by shirilover on 2008-06-05
You may need to check your email for a confirmation code.
Or follow what ever happens with the output from
/ns help identify

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-08
Hm! For another private reason, I had reinstalled Ubuntu and my applications... This time, I followed the Smogon tutorial and everything went smoothly:confused:

Thanks for your help anyway guys!
Armageddon.

---

