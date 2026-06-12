---
title: "Point me in the right memory direction"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by its_jon on 2008-09-14
Hi..

I now know that linux uses memory in a more efficient way than windows by actually using it more to speed things up....

I just upgraded from about 700meg to 2 gig memory so I can enable more desktop toys ect.

I notice that the memory is rising 3 quarters of the way into my 2 gigs now....

I have 855.0 mbs of swap unused at the moment..

Before I upgraded to 2 gig memory it hit the swap very quickly and the only way to recover was to reboot ubuntu.

It looks as though I will eventually hit the same situation with my 2gig of memory ..... how can I stop it maxing out the memory ?
I don't want to reboot every 48 hours to flush the system... I like to leave my PC on 24/7

Anyway..... I guess there are probably some excellent threads (or tutorials) that discuss this already ... could someone please point me to one of the better ones as I am struggling to find something more specific probably because im not too sure what I should be searching for.

---

### Post by bobnutfield on 2008-09-14
I doubt that you will be hitting your swap partition with 2GB of memory unless you are doing some extremely memory intensive tasks.  When you type:

> free

in a terminal, the amount of memory shown in "cache" is on-call and available.

---

### Post by k33bz on 2008-09-14
nvm

---

### Post by Thingymebob on 2008-09-14
Memory not being used is wasted. Put simply Linux will keep stuff in memory until there is no space left then start paging to the swap. Remember memory is much faster than HDD so keeping stuff in RAM = better performance. Keep adding it and You'll keep filling it.

---

### Post by Oldsoldier2003 on 2008-09-14
In a nutshell: the Linux kernel caches programs and data into RAM and leaves it there for reuse. High memory usage is by design, swap is only used when absolutely necessary.[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) is a nice link to help explain the subject.

---

### Post by its_jon on 2008-09-14
Yes... I understand that it uses memory to its fullest which is good !

Maybe I have a memory issue.... as whenever I hit swap the system starts to slow down. 
I would have assumed this would be the point linux should stop loading up the memory.

I close anything thats open
I enter system monitor and start to shut stuff down
But end up having to reboot as the memory usage is still maxed

Could I have set up the swap incorrectly in some way ?

edit: thanks for link Oldsoldier2003

---

### Post by Thingymebob on 2008-09-14
> **its_jon said:**
> edit: thanks for link Oldsoldier2003
Nice link old soldier.

[its_jon] i'm not sure here, your join date indicates you're not completely new to Linux so i'm guessing you've already checked your swap entry in /etc/fstab is correct and that your swap partion is formatted as swap?

I always used to stick swap in the middle of the drive so as the heads had less distance to travel to access swap regardless of their current position though this makes little difference with modern hdd speeds.

you could also do:
(replace ***/dev/hda2*** with whatever your swap is)
**[SIZE="3"]_[COLOR="Red"]make sure you get the right partition[/COLOR]_[/SIZE]**
mkswap doesn't check that the partition isn't already being used for something else
```

swapoff /dev/hda2
mkswap -c /dev/hda2
swapon /dev/hda2

```

which will turn off your swap then recreate, checking for bad blocks first

---

### Post by its_jon on 2008-09-15
Thanks for the info....

Yes... I joined this forum years ago and have come back for support on 2 or three occasions when I have tried to get Linux up and running... however I have never stuck with it until now.
I think this latest version of UBUNTU is fantastic with almost everything working out of the box....most issues have been simple for me to correct this time round unlike previous attempts to use UBUNTU.

I have a large drive with XP on.... the Linux drive is only 20k (my older drive) which actually spins quicker..... When I set up Linux I have to admit I really don't have a clue what the partition setup was I was so paranoid that my XP drive was left untouched that was all that mattered (as I used XP for work)....

So.... apart from the XP having no Linux partitions im not really sure whats going on with the 20 gig unit.

Very much on a voyage of discovery this time unlike previous attempts.... fully enjoying the UBUNTU experience....so bear with me.

What I can see myself doing in some months time using this rock solid UBUNTU !!.... is finally backing up my XP drive and wiping it for Linux use as storage.... Its a 80gig unit (late design 'fixed') deathstar drive.

So.... any suggestions about the best way to use these two drives in the future ? ..... My Ubuntu install on the 20gig unit is starting to feel very personal already so I feel as if I should keep it just for the OS with programs and files stored on the 80 gig unit.... Is this possible or indeed a easy or optimal thing to do ?

thanks
John
Scotland

---

### Post by nowshining on 2008-09-15
try this,

sudo gedit /etc/sysctl.conf

add the following:

#set swappiness to zero/50%
vm.swappiness=0

save/exit

in terminal do sysctl -p

---

### Post by its_jon on 2008-09-19
what does it do ?

I would like to know first.... thanks.

:)

---

### Post by nowshining on 2008-09-19
it makes the system use up all the ram before going to swap or suppose to :)

---

