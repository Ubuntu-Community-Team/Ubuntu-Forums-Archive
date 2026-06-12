---
title: "Strange Problem"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by wesireal on 2011-09-14
Hi,

I am old,not clever and complete newbie. Please help.

I was using a self assembled PC with:

Mobo:Asus--M4A78LT-M
CPU: AMD AM3 Phenom.
Video card:ATI/AMD Radeon 5xxx

Yesterday I installed Ubuntu 11.04  64bit.All went well. Checking applications I saw Additional Driver for the video card---Something to do with 3D rendering so I clicked to install.It was installed without problem and then the system ReStarted.All well.After I listened to music on the pc,played Hearts and surfed the net for about an hour.Then I shut down pc and went to sleep.

Today I started the pc in the usual manner.It started but the monitor remained black. I know the pc was running because I see the cpu fan working.Also this mobo has a green light in the middle to show that the board is functioning fine. So I tested the monitor  Samsung SyncMaster 245a plus, with my 2nd pc.It is working fine.

The screen is black while the pc is on and whizzing.

Please,please help.What should I do?:confused:   
Edit: I just tried to check my profile to check if I have the email address in use now but I was not allowed to get in.I am subscribed to this thread.I hope my account has my Gmail account,otherwise the notice will not reach me.Sorry about this.

---

### Post by CharlesA on 2011-09-14
The profile thing is to help prevent spam. Your account email is a gmail address.

It sounds like the proprietary drivers caused a problem of some sort. Are you able to boot into safe graphics mode from recovery mode? Hold down shift while the machine is booting and then select recovery mode from the menu.

---

### Post by DSn0wMan on 2011-09-14
Sounds like the driver you installed isn't working. It wouldn't have taken effect until after restarting the X-Server which surely happened since you rebooted.

Still I am not sure why you wouldn't at least get a fail-safe mode.

Try hitting ctrl+alt+f2 to get to a terminal. If you get that far there are commands you can run to reconfigure the x-server

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by pierreyy on 2011-09-14
check the connection between the monitor and the pc... maybe it was loose... if not its probably a driver error

---

### Post by wesireal on 2011-09-14
Thank you all.

It is late now.I will try what you have suggested and report back.

The connection was the first thing I did.It was fine .:D

PS: If I do get some video what is the way to remove the driver?Please.Or is there a way to system restore to a previous day like in windows?

---

### Post by CharlesA on 2011-09-14
You'll have to remove the driver manually. Not sure which one it is tho as I don't have an ATI card.

---

### Post by wesireal on 2011-09-18
Sorry for the delay, was not feeling well.

I changed the memory and thinking hdd was gone as well and because I had no data at all,I swear I put in the  KillDisk and waited 4 hours to do its thing.

I had bought a new hdd.I connected the pc just now withought thinking about the new hdd.Same old problem no video signal.Please do not ask why,my age,
but I inserted a Hiren's Boot cd of May 2008. It revolved and then nothing but a moment later the screen went purple and,lo and behold good old Ubuntu 11.04 64 bit booted and I am usin it for this post.

As I said in the begining and do not really understand electrical contraptions.If my age has taught me anything it is,not to waste time on matters I have no knowledge.So what did happen?No exaguration above.

I am grateful to all of you for the prompt attention and advice.

Thank you

---

