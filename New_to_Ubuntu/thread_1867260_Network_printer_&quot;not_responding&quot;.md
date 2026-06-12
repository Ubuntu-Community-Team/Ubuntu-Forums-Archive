---
title: "Network printer &quot;not responding&quot;"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-10-22
I have a Canon Pixma iP4300 printer connected by USB to my main PC running Ubuntu 11.04.
It works OK.
It is "shared".
The PC has a wifi connection to internet.

I recently got a Netbook with Windows7 which uses the same wifi connection OK.
After a bit of fiddling with Samba, W7 can now print via the main PC OK.

Then I added Ubuntu 11.10 to the Netbook & expected printing to be simple...
Actually, I added the printer to the Netbook OK, using "add > Network Printer" - it found it automatically & it shows up as default printer.
The device URI appears as "dnssd://iP43003cups%"
Under "Make & Model", I navigated to a driver for iP4300 OK.

But no printing.
Jobs, including Print Test Page, get to the print queue & the printer status changes from: 
"Idle - The printer is not responding" to:
"Processing - Printing page 1 - 7%" or some other%, then:
"Processing - The printer is not responding".
I also get warnings that the printer "may not be connected".

I would appreciate any help in diagnosing this problem.

Thanks!

---

### Post by Shazaam on 2011-10-22
Unity...
Windows (super) keyboard key (opens Dash)- enter (or find) Printing and run it. Right-click your printer and choose "Properties/Access Control". Do you have that configured?

---

### Post by wylfing on 2011-10-23
I just encountered something like this on my wife's 11.10 Ubuntu. She wanted to print to a printer connected to my machine (Kubuntu). The add printer screens seemed to find it right away, but it always errored out with printer not connected.

So I deleted the printer and started the add process over again, only this time I picked IPP from the network printer list, and entered the ipp address manually. You can find the ipp address by going to [http://host:631](http://host:631) where "host" is the name or IP address of the computer where the printer is attached. Click Printers and then click the name of the printer you want to print to. The URL that's in your browser bar is the ipp address, except you need to change "http" to "ipp".

Ninja edit: Forgot to say that it prints just like it should using the ipp method.

HTH

---

### Post by 2CV67 on 2011-10-24
> **Shazaam said:**
> Right-click your printer and choose "Properties/Access Control". Do you have that configured?
I selected "Allow printing for everyone..." if that is what you mean - yes.

---

### Post by 2CV67 on 2011-10-24
> **wylfing said:**
> 
So I deleted the printer and started the add process over again, only this time I picked IPP from the network printer list, and entered the ipp address manually. You can find the ipp address by going to [http://host:631](http://host:631) where "host" is the name or IP address of the computer where the printer is attached. Click Printers and then click the name of the printer you want to print to. The URL that's in your browser bar is the ipp address, except you need to change "http" to "ipp".

Thanks very much, wylfing, for your suggestion!
I struggled slightly with your short instructions, then found a page saying the same thing in more detail:
[http://gain4you.net/info/309/how-to-share-printer-over-ubuntu-network/](http://gain4you.net/info/309/how-to-share-printer-over-ubuntu-network/)

Following that (same as you said, but easier for a dummy to follow - didn't change http to ipp though) - & it works! :D

Only remaining questions are - why did I have to do that & where should I have found out how to do it?
What happened to "It just works"???  :confused:

Thanks again, wylfing (& Ubuntu community in general)!

---

### Post by wylfing on 2011-10-25
Sorry about the meagerness of my explanation, I typed it up in a real hurry. Glad you were able to find better instructions.

As for why, my suspicion is that the network printer applet is trying to connect over protocols that are maybe a little too forward for the rest of the universe. That's why using the older IPP method worked. I wouldn't be surprised if it works fine so long as both machines are running Ubuntu 11.10.

---

### Post by AaronRGod on 2011-11-14
I can confirm 2CV67's issue, and both my desktop and server are running 11.10.

wylfing's solution works for me; thanks a lot!

---

### Post by John Peschken on 2011-11-14
I have had a similar phenomenon on my system.  I am connected to a D-Link DPR-1260 wireless print server as an LDP printer.  I get warnings that the printer "may not be connected".  It _is_ slow to start, but it always prints shortly after Ubuntu starts getting all worried.
  
Everything works fine in the end, so this is only an aesthetic problem.  Is there an easy way to increase the timeout so Ubuntu calms down about that printer?

---

### Post by Joliea on 2012-03-13
Hi,

I have the same problem only for my case, I've properly installed the printer(s) but once in a while it says "held" in the printing queue and I have to open the printing queue to 'unhold' it. It sometimes takes me about ten minutes to print one document!

Another issue is that the print queue used to show on the top right had side of the screen next to the 'messaging' icon. Nowadays it doesn't show. Anyone who can assist me in getting it to show whenever I've sent something to print? I always have to go to dash, search for "Printing" to see the printing queue. Its tiring.

Thanks.

---

