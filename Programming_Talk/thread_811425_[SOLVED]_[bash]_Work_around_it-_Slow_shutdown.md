---
title: "[SOLVED] [bash]: Work around it- Slow shutdown"
date: 2008-05-29
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-05-29
Lady and gentlemen,


I have a little issues w. Ubuntu after discarding my initial 7.10 install. When I click the "Shutdown" icons, the system (input/output) seems to freeze completely for about 3 - 5 minutes, whereafter the shutdown dialog will appear and I can shut down. After doing much reading I find that this is usually because of an incorrectly configured loopback device - this doesn't seem to be that case here, as it looks correctly configured. (anybody know of a test for this?).

So, to work around this issue, I wanted to make a little script which did a "sudo shutdown -P now", and simple type "bye" in the terminal to shutdown. But how do I form the script if I want to automatically feed the sudo-password to the command? I've tried something like echo "topsycrets" | sudo shutdown", but it doesnt do the trick.

Any suggestions for either loopback or bash workaround?

/Lau

---

### Post by Thanoulis on 2008-05-29
If you want, you can shutdown your pc, without typing any password...
Just edit your /etc/sudoers file:
```
sudo visudo
```
Then, add the following line:
```
%<your usename> ALL=(ALL) NOPASSWD: sudo shutdown -P now
```
(or any other command you want).
Hope this helps!

---

### Post by Lau_of_DK on 2008-05-29
> **Thanoulis said:**
> If you want, you can shutdown your pc, without typing any password...
Just edit your /etc/sudoers file:
```
sudo visudo
```
Then, add the following line:
```
%<your usename> ALL=(ALL) NOPASSWD: sudo shutdown -P now
```
(or any other command you want).
Hope this helps!

It seemed like a good idea at the time! :)

After appending that line to the /etc/sudoers, sudo has stopped working. It says ">>>> sudoers file: syntax error, line 23 <<<<" - How do I recover from this? I cant even edit the file with the rights I have now.

/Lau

---

### Post by geirha on 2008-05-29
1. Boot into recovery mode and run visudo, or
2. Boot the liveCD, mount your / to /media/disk or wherever, and run ```
sudo chroot /media/disk
``` Then, inside chroot, run visudo.

The reason it didn't work, is because the syntax is wrong. The first field should be either "%<group>" or "<username>" (without %). You should read the manpage for sudoers for a full doc, ```
man sudoers
```

---

### Post by Lau_of_DK on 2008-05-29
> **geirha said:**
> 1. Boot into recovery mode and run visudo, or
2. Boot the liveCD, mount your / to /media/disk or wherever, and run ```
sudo chroot /media/disk
``` Then, inside chroot, run visudo.

The reason it didn't work, is because the syntax is wrong. The first field should be either "%<group>" or "<username>" (without %). You should read the manpage for sudoers for a full doc, ```
man sudoers
```

Alright - I was hoping there was a way around booting (lazy I know), but at least it will work - I hope. I'll let you know on the other side.

Thanks for the explanation of the sudoers file.

/Lau

---

### Post by Lau_of_DK on 2008-05-29
I tried replacing the % with nothing, so just the username, it didnt work. Then I tried "username ALL=NOPASSWD: sudo shutdown -P", and that didnt work either, but at least I have sudo rights again.

Can anybody tell me the correct syntax for giving me sudo access to shutdown -P now, w/o entering the password?

/Lau

---

### Post by geirha on 2008-05-29
Oops, didn't notice that earlier, but you shouldn't have sudo in there
```
username ALL=NOPASSWD: [color=red]sudo[/color] shutdown -P now
```
That would produce an infinite loop, since it reads /etc/sudoers each time you run sudo ...
```
username ALL = NOPASSWD: shutdown -P now
``` really should work.

Also, note that the position in the file is important. From the man-page of sudoers:
```

       When multiple entries match for a user, they are applied in order.
       Where there are multiple matches, the last match is used (which is not
       necessarily the most specific match).

```

---

### Post by Lau_of_DK on 2008-05-29
Its really weird! 

I tried 
```

username<tab>ALL=NOPASSWD: shutdown -P now
username<space>ALL=NOPASSWD: shutdown -P now
username<tab>ALL<space>=<space>ALL=NOPASSWD: shutdown -P now
username<space>ALL=(ALL)<space>ALL=NOPASSWD: shutdown -P now

```

...and so on.. every single combination gives me a parse error...:confused:

/Lau

---

### Post by geirha on 2008-05-29
It's been a while since I messed around with sudoers, but I think I found it now. The command needs to be represented with an absolute path (which is obvious when you think of security). So
```
username ALL=NOPASSWD: /sbin/shutdown -P now
```
Hopefully that's the final change to the original line ;)

And remember it needs to be before the general ```
%admin ALL=(ALL) ALL
``` line.

EDIT: No wait, I've misread the man-page, it should be after the %admin ALL...-line

---

### Post by Lau_of_DK on 2008-05-29
Alright, so to sum if this awful thread :)

```

username ALL=NOPASSWD: /sbin/shutdown -P now

```

Actually works - So thanks alot for all the help!! :)

To Thanoulis: Dont feel bad, even the best of us make mistakes and I thank you for trying.

/Lau

---

