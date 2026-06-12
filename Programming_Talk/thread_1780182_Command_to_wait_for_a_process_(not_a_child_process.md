---
title: "Command to wait for a process (not a child process)"
date: 2011-06-11
forum: Programming Talk
---

### Post by Paddy Landau on 2011-06-11
If I create a detached process, I can wait for it to finish using the *wait* command. E.g.
```
~$ [COLOR=Navy]gcalctool &[/COLOR]
[1] 8822
~$ [COLOR=Navy]wait 8822  # Sleeps until gcalctool terminates.[/COLOR]
```But what if I want to wait for a process that is not a child process? E.g.
```
~$ [COLOR=Navy]ps -e | grep -F gcalctool[/COLOR]
 8830 ?        00:00:00 gcalctool
~$ [COLOR=Navy]wait 8830[/COLOR]
bash: wait: pid 8830 is not a child of this shell
```The only solution I have come across is to use a loop in a script. A basic example would read:
```
while [[ ${?} == 0 ]]      # Repeat until the process has terminated.
do
    sleep 10s              # Wait a bit before testing.
    ps -p 8830 >/dev/null  # Check if the process has terminated.
done
```Is there no command that will wait for a non-child process?

---

### Post by TeoBigusGeekus on 2011-06-11
```
[[Time:23:30 Location:~/Desktop]]
$ pgrep gcalctool
15435
[[Time:23:31 Location:~/Desktop]]
$ while [ -e /proc/15435 ]; do sleep 0.1; done
```

---

### Post by Paddy Landau on 2011-06-12
@TeoBigusGeekus:

Hey hey, I learn every day! Thank you for the greatly simplified version. I shall replace my existing loop with this.

It is still a loop, though. Isn't there a non-loop option equivalent to *wait*?

---

### Post by TeoBigusGeekus on 2011-06-12
Not that I know of, sorry...
If anyone does, speak up or forever hold your silence.

---

### Post by Paddy Landau on 2011-06-12
> **TeoBigusGeekus said:**
> If anyone does, speak up or forever hold your silence.
I don't think there is. I have Googled extensively, without any success. Maybe it's a permissions thing.

---

### Post by SDSukhani on 2012-02-08
Hello sir, I just wanted to know what do -e does of your -e /proc/ command.
Would be thankful for your precious help.

---

### Post by jwbrase on 2012-02-08
> **SDSukhani said:**
> Hello sir, I just wanted to know what do -e does of your -e /proc/ command.
Would be thankful for your precious help.

It tests if a file exists. Check the manpage for "test", which can also be written as [ <whatever you want to test> ]

---

### Post by SDSukhani on 2012-02-21
Thanks a lot sir!

---

