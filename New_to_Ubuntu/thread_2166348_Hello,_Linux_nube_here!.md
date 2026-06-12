---
title: "Hello, Linux nube here!"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by Boomer8404 on 2013-08-08
Hi all, as I said in the title, I'm pretty much a nube at Linux. I have never used it before until around 3 weeks ago. I built a secondary computer out of my old system that I am running as a server for Minecraft Bukkit, music & video media and file backup. I have successfully gotten the Minecraft portion of my server computer setup but, not the rest. 

Currently running Linux Ubuntu 13.04, I have done a little research as far as server FTPs go, and have looked at vsftpd, proftp & pure-ftp. I'm not really skilled at working with the Terminal. I would really prefer to use an ftp that has a GUI, as again, Im not really familiar with the use of the Terminal. I know on the Ubuntu Softwar Center, there is PureAdmin FTP GUI.

As far as futher requirements, I am wanting to control access with Username and Password account access so the server is not open to the public. Also, for data storage, I currently have a 3TB backup drive currently installed for use, and I will be adding 3 more 3TB drives for further storage as time goes by. I dont particularly want the main drive accessible to outside users. I only want the current 3tb drive and the other 3, 3tb drives that I plan to be adding in the future (if that is so possible).

I would like to know if anyone has any suggestions for an FTP server to use other then what I have listed. And, or if there might be one better/easier to setup. Oh and before I forget, all clients logging into my Linux server computer will be Windows systems so I would need an FTP client for Windows thats compatible with the Linux server FTP.

Thanks for any time, sorry for the long read but, I really need some help.

---

### Post by mastablasta on 2013-08-09
FTP is protocol (File transfer protocol) so any windows FTP client will work. including file explorer or whatever it's called now.
i would suggest to maybe try filezilla (both clients and servers are good). 

if you are looking for a GUI server on the other hand then try:

Zentyal (Ubuntu LTS based)
Openmediavault (debian based)

or simply install ubuntu server and then add webmin to it.

for server it makes sense to use LTS edition. that way you can prepare porpperly to do the upgrades. as normal releases only have 9 months support.

---

