---
title: "Easily connect to a PPTP server using Network Manager"
date: 2008-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by megamaced on 2008-07-09
1.) First we must install the pptp plugin for Network Manager:
[INDENT]
Open a terminal and type:

```
sudo aptitude install network-manager-pptp
```[/INDENT]

2.) Left click the Network Manager applet in the system tray and point to VPN Connections, click "Configure VPN" and choose "Add".

3.) Click "Forward", then ensure PPTP Tunnel is selected and click "Forward" again

4.) Choose a Connection Name and enter the IP address of the PPTP server under Gateway.

5.) Click the "Authentication" tab and tick "Authenticate Peer". Then untick either EAP, CHAP or MSCHAP. **DO NOT UNTICK MORE THEN ONE OR IT WILL NOT WORK!** For example, if I want to connect to an PPTP server with MS CHAP authentication, my configuration will look as follows:

[IMG]http://img295.imageshack.us/img295/9923/nmencryptiondt0.jpg[/IMG]

6.) In the Compression & Encryption tab, ensure all boxes under Compression are unticked.
In the Encryption section, choose whether to require MPPE encryption. If you are connecting using CHAP, you should only need to tick Enable MPPE stateful mode and leave the other options unchecked. If you are connecting using MS CHAP, you may need to tick require MPPE encryption.

7.) The options under the PPP Options and Routing can be left at their defaults.

8.) Finish the PPTP wizard

9.) You should now be able to connect to your VPN. If you can't see your new PPTP connection under the VPN Connections menu, you may need to restart your computer before it will appear. I think this is a bug..

10.) Should your PPTP connection be unsuccessful. I'd advise checking the Messages log (System > Administration > System Log)

---

