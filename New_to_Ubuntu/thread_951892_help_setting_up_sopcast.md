---
title: "help setting up sopcast"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by craiggale on 2008-10-18
i installed sopcast and the gospcast gui using 

cd ~/Desktop
wget [http://download.sopcast.cn/download/sp-auth.tgz](http://download.sopcast.cn/download/sp-auth.tgz)
tar -zxvf sp-auth.tgz
cd sp-auth
sudo cp sp-sc-auth /usr/bin/sp-sc

and all worked fine, however i could not choose a channel manually so i installed spolaunch but i couldn't get this to work possibly because i don't have the right version of sopcast? so i removed it. 

now when i load the gsopcast gui i don't get any channels appearing when i try to start streaming a channel threw the command line i get this 

craig@craig-laptop:~/Desktop$ tar -zxvf sp-auth.tgz
sp-auth/
sp-auth/Readme
sp-auth/sp-sc-auth
craig@craig-laptop:~/Desktop$ cd sp-auth
craig@craig-laptop:~/Desktop/sp-auth$ sudo cp sp-sc-auth /usr/bin/sp-sc
[sudo] password for craig: 
craig@craig-laptop:~/Desktop/sp-auth$ sp-sc 
SC Version: 3.0.1  Build time: 2008-03-20 11:25
Usage:
./sp-sc [-T] [-t seconds] [-u username:password] [-n out:total] [-x suffixname] [-a [http://auth_url]](http://auth_url]) <sop://url> <localport> <playerport>
craig@craig-laptop:~/Desktop/sp-auth$ sop://broker1.sopcast.com:3912/30931
bash: sop://broker1.sopcast.com:3912/30931: No such file or directory
craig@craig-laptop:~/Desktop/sp-auth$ cd
craig@craig-laptop:~$ sp-sc sop://sop.sopcast.org:3912/30931 3908 8908
detect MTU=4c4
Connection=11	Connection=11
i=0   51
ipExternal:bd521956  Internal:400000a  portLocal:41480    portExternal1:41480    External2:41480  linkType:51
tm2.sopserv.com proto=17
adv=738
TD1=4294967168-128:  1224356985:738:291305030
tm2.sopserv.com proto=17
adv=351
TD1=4294967168-128:  1224356985:351:291305417
Average difference=4294967168
4294967168
4294967168
3dbedaf0 28ba0b0d
Not valid ID
db391e9c 73ae408c
sop://sop.sopcast.org:3912/99
system channelID=99
channel ID=30931
tk:00000000 00000000
streamID=78d3
Error broker hostname can't be resolved
sopch2_schedule_sc_misc_sysch retv=-100
CHLST blockSize=0
291306319:291305290
Error broker hostname can't be resolved

any ideas why?

---

