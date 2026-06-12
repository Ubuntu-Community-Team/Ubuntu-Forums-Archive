---
title: "Security and Passwords Ubuntu 12.04"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by Tahinimoon on 2012-07-10
Hi, 
I am not very adept at using the correct terms so please bear with me. 

Today something really strange happened on my pc: (I use Firefox browser)
1. My open browsers just shut down and my Internet Server Providers main page popped up.
2. The page said that there were already too many connections open (error 604).
3. I called my service provider and they checked - they asked me to reset my router and thereafter it was fine again.  They were quite perplexed as to what had occurred and suggested I keep a check on it. 

Since then I've been doing some reading to determine what could have happened and can't find anything that is really helpful. 

So my questions are:
1. Can someone outside of my home be accessing my connection?
2. Does this have 'anything' to do with Ubuntu and the security of my pc?
3. I do not have a clue how to change all the passwords: (I have changed my email password) But there is also the 'appy authentication' password. Apparently if i change that password I also need to change another password -to do with the key rings???
4. Somewhere else it is suggested i check how many ports are open - how do i do that and what difference does it make?
5. Somewhere else i read that i need to have a firewall? I thought that was not necessary? If it is which one and how do i instal it? I do have 'clamscan' which I do run every now and then via the terminal. - is that enough ?
6. I have removed the Bluetooth appy. I don't have a laptop and i don't use my cell phone to connect I use my landline. 

I am not tech savy - so trying to make sense of what seems to be an ongoing debate about whether one needs a virus protection programme or not is just beyond my grasp. 

Can you please advise me?

---

### Post by Cheesemill on 2012-07-10
Do you use torrents at all?

Torrenting can open a massive number of connections.

---

### Post by Rodney9 on 2012-07-10
check your security here - [http://tinyurl.com/sovd](http://tinyurl.com/sovd)

Rodney

---

### Post by Laiquendi on 2012-07-10
About your questions: 
1. Can be. But we need more info about your internet situation - do you have a wi-fi router? If not - not possible. 
2. If you're not into some very strange software then breaking into your ubuntu is almost equal to zero chances. We can't be 100% sure, but you should first consider other possibilities. 
3. If you change passwords, you'll have to write them first by hand and ubuntu will learn them if you let him do that. 
4. If you have too many ports open then the issue is in your computer, not somewhere outside. Can you use terminal/command line or do you strongly prefer graphical tools? 
5. If you have too many ports open then yes firewall may help 
6. Emm not much of a question ;)   

So to sum up: 
Do you have torrents? Do you use any other heavily connection-utilizing software?

---

### Post by Tahinimoon on 2012-07-10
Hi, 

Thanks for the responses.  Just for clarity - I have a Desktop pc - no laptop. 

1. When you say Wi-fi I am assuming you mean 'wireless' ? - I connect to the internet with a modem - cables  are plugged into my pc and into the modem.  So does that mean that no one can use my internet connection? That would be a relief. 

2. I can use the terminal to enter command lines - if I copy and paste them. :}

3.  I do use bit-torrent - and recently - did so quite a bit.  So I am assuming that because I had been using it a number of connections were opened - which would account for what happened possibly? But when i close down bit torrent it says that it's shutting down the connections? 

[LEFT]4. I checked my security at the link given - I do not understand the result. :(
"[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000060]If  the machine name shown above is only a version of the IP address, then  there is less cause for concern because the name will change as, when,  and if your Internet IP changes. But if the machine name is a fixed  account ID assigned by your ISP, as is often the case, then it will  follow you and not change when your IP address does change. It can be  used to persistently identify you as long as you use this ISP."   I am registered with a reputable ISP Provider. I do not know if my 'machine name' is fixed or not - I have reloaded the page a few times and the name remains the same. 

5. I don't want to change passwords unless I have to - should I change them every now and then?

6. Sorry - re: the bluetooth appy i said I removed - I thought that perhaps if someone has bluetooth - eg: someone in my area - that they could perhaps use my internet connection from a laptop and cell phone. Or is that just a bad understanding on my part?


[/COLOR][/SIZE][/FONT][/LEFT]

---

### Post by Tahinimoon on 2012-07-10
..... and how do I close those Torrent connections - or ensure they are closed? What do I do in the future when using bit torrent?

---

### Post by Laiquendi on 2012-07-10
1. I mean wireless :) If you have wireless turned down (no antenna, router radio off, depend on situation...) then yes, if someone wants to use your connections he/she would have to make a hole in your room to put a wire ;)
4. So it is fixed - it's common, click "proceed" and the you'll have to click 2 more buttons and the results will be shown in a human-understandable way (text) and in "geek" way ;)
5. Sometimes you should, it's up to you how much secure passwords you use and how danger it is to have them cracked.

If you don't use bluetooth keep it turned off - simple and secure way.

Torrent app you used might be the problem. Try to configure it different (in manual according to your program there should be instruction how to do it to make less connections). Also your ISP may be blocking torrent and sometimes in result - cut torrent users form the net.

Hope it'll help!

---

### Post by Rodney9 on 2012-07-10
When I check my security here - [http://tinyurl.com/sovd](http://tinyurl.com/sovd)

I get -

> Your system has achieved a perfect "TruStealth" rating. Not a single packet &#8212; solicited or otherwise &#8212; was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

That is what you want.

---

