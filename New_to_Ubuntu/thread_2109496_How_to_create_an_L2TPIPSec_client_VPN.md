---
title: "How to create an L2TP/IPSec client VPN"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by waltd on 2013-01-27
Hi all,
   I'm a newbie to Ubuntu and Linux.  I have Ubuntu 12.10, 64bit with Unity desktop.  I have an account with a VPN provider and I am a client only (not a server).  

   How can I create a L2TP/IPSec VPN connection to my VPN provider?  I noticed that Ubuntu's "VPN Connections" only has an option for PPTP.  However, I would like to create a L2TP/IPSec VPN connection to my VPN provider.  Thanks.

---

### Post by DuckHook on 2013-01-28
Most VPN providers have instructions for connecting from a Linux client. I would suggest that you visit the web site of your provider for instructions.

If you want general instructions, they are [here]("https://help.ubuntu.com/community/VPNClient").

I strongly discourage the use of PPTP. It is worse than useless because it gives the illusion of security while providing none. IPSec is better, but not by much. Many VPN providers will support certificate-based VPN which is the best choice.

---

### Post by waltd on 2013-01-28
Thanks DuckHook,  It seem that installing L2TP/IPSec is not easy on Ubuntu.  Before I posted my question, I did check out the provider's suggestion but he was not too helpful.  He pointed me to a very technical document that's for an earlier version of Ubuntu.  So, I'm trying to approach the solution from many sides.     
  
I agree with what you said about PPTP.  I never use it.  The reason I'm focused on L2TP/IPSec is because I'm currently living in a country that blocks OpenVPN and PPTP with Deep Packet Inspection (DPI), so I have to use L2TP/IPSec.  Again thanks.     
[]("http://ubuntuforums.org/member.php?u=1256508")

---

### Post by frank604 on 2013-01-28
Hey Waltd, we meet again!  Hope your adventures in Ubuntu are rewarding :)

Please post the guide he sent to you.  Also, do try to follow them knowing that many of the steps might be outdated.  Doesn't hurt to follow the objective or end goal with your current version of Ubuntu.

For example, if the goal is to get across the lake an older ubuntu might have used travelling on a boat as the method but the current ubuntu might use a bridge as the method.  The goal is the same. 

If anything funky happens, post them on the forum.  Sorry I can't be of help for this one at the moment with the lack of VPN knowledge.  Maybe other's will have a better go at it.  Post the guide either way.

---

