---
title: "System problem detected"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-11-21
okey today i had a huge problem with m y ubuntu system i dont know whats really happend but suddenly it freezed i am not sure even i could finish this messsage but there was a error says GPU freeshed crashed o r something like that but i never had a that kind of erorr before it worked perfectly my ubuntu system is a 64 bit 2.00GB ram 3.00GHZ dual core e5700 500GB alog sinde windows xp

when that issue happen my cpu usage 2 Cores went to 100% i restarted i got that system problem detected erorr now its normal i thin k whats that ? do i need to remove ubuntu i dont know anything about linux system settings etc


here is the error

Apport has detected a possible GPU hang.  Did your system recently lock up and/or require a hard reboot?

[https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-ash3/574447_3914863471672_1301080882_n.jpg](https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-ash3/574447_3914863471672_1301080882_n.jpg)

my VGA is intel G41 express
the error details showing me the problem with the GPU 

 Apport has detected a possible GPU hang.  Did your system recently lock up and/or require a hard reboot?




the pop up is not appearing continuesly what do i do 

and one core is 100% cpu usage now its starts in every time i restart the pc what happend it never happend before

---

### Post by Bashing-om on 2012-11-21
vibaviattigala; Hi !

I am admittedly not the sharpest tool in this tool box,
However, In this situation I would execute the terminal command:
```
top
``` and observe for the process that is consuming the resources. [type "q" to quit it]
then I would force a file system check on next boot
```
sudo touch /forcefsck
sudo shutdown -r now

```Then again when booted up:
```
top
```and compare before/after results.
[INDENT][INDENT]try'n to help <==BDQ

[/INDENT][/INDENT]

---

