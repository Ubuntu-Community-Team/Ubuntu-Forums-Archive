---
title: "duel boot ubuntu and windows 7"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by wangwangster on 2012-12-31
Hello guys thankyou for reading my first post

I am not sure if the title i posted is correct or misleading but this is what i want to achieve.
i currently have windows 7 set up on a ocz 120 gb pci express ssd this is my C drive and i have 2 x 1 TB drives for storing data and other things, I have just picked up a 500gb seagate drive and wondered if i could install ubuntu on this drive and have whats called a duel boot capability. Before i do this i am wondering what issues i my come up against, and how i can avoid any disasters as i have never done anything like this before. I am assumeing if this is possible it will be a simple matter of choosing which operating system to run at boot time and away i go on either ubuntu or windows 7. sorry if my exspectation seems simple but agan i ve never tried this before.
My system specs are as follows if this helps

2 x xeon 5650 processors
24 gb ram
supermicro motherboard
120 gb ocz pci express ssd
2 x 1 tb wd drives
1x 500gb sg drive
DVD drive.
nvidia fx 4800 graphics card

thank you for taking the time to read my thread and i look forward to your responses and guidence

wangwangster

---

### Post by Frogs Hair on 2012-12-31
Hello and Welcome

I dual boot with a single hard drive and almost everything that has come up was covered at the link . What was not covered was addressed in threads here on the form. I've re-installed the Grub boot loader which is addressed in the text.      [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Old_Grey_Wolf on 2012-12-31
[Here]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/") is a tutorial for dual booting Windows 7 and Ubuntu 12.04 from two hard drives. 

Be sure to make a backup of important files before you set up dual boot, especially since it is your first time. Also, make sure you have your Windows DVD ready just in case you have to fix Windows if a mistake happens.

With that much CPU power (12 cores) and Memory (24 GB), you may want to use [virtualization]("https://www.virtualbox.org/wiki/Virtualization"). With virtualization you can have multiple operating systems running at the same time. Oracle's [VirtualBox]("https://www.virtualbox.org/") is an easy one to install. If you like VirtualBox then you can try other virtualization methods that are more efficient; however, harder to install and configure.

With that machine you should be able to run 6 operating systems at the same time. You could have Windows 7, an evaluation of Windows 8, Ubuntu 12.04 Long-Term-Support, and three other distros you want to try out. All without having to reboot your computer.

---

### Post by wangwangster on 2013-01-01
thankyou for your replys i will check out the links you have pointed out, 
thank you old grey wolf i will do some research on virtualisation and make some more decisions as what to do i really want to learn back track, but have been advised to start with ubuntu first as i am a complete beginner. 
Yes and thankyou my computer is a bit of a beast i built it because i do alot of computer generated graphics for my hobby. but i want to learn some programing things also.

thanks you for all your advice guys i am sure i will have more questions soon

---

