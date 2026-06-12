---
title: "Unable to make an upstart job for this"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by nitrosrt10 on 2013-12-30
I have to start a task by using the ssh access to my 12.10 vps, the task is ran by launching this in the ssh terminal: ./sc_trans sc_trans_mrs.conf
Now I have to keep the terminal window open in order to run this task, because as soon as I close the ssh terminal the tasks stops.

Another problem is that it doesn't run if I do this:
/root/pleasehelp/sc_trans sc_trans_mrs.conf

I HAVE to do this to run it:
cd /root/pleasehelp
./sc_trans sc_trans_mrs.conf

The reason behind running this as a daemon is that I want to make it a upstart job but since /root/pleasehelp/sc_trans sc_trans_mrs.conf doesn't work, I am unable to make a upstart job for it.
This is what I tried last time and as expected it didn't worked.
```

# aaa
#
# common


description  "common"


start on runlevel [2345]
stop on runlevel [!2345]


pre-start script
    cd /root/shoutclient


end script


exec ./sc_trans sc_trans_mrs.conf

```

P.S. I tried chmod +x sc_trans but it didn't helped.
P.P.S. I am really frustrated.

---

### Post by ian-weisser on 2013-12-30
> **nitrosrt10 said:**
> I have to start a task by using the ssh access to my 12.10 vps, the task is ran by launching this in the ssh terminal: ./sc_trans sc_trans_mrs.conf
Now I have to keep the terminal window open in order to run this task, because as soon as I close the ssh terminal the tasks stops.

If you want to keep the job running after you logout from a session, look at the *screen*, *screenie*, *tmux*, or *byobu* packages.


> **nitrosrt10 said:**
>  Another problem is that it doesn't run if I do this:
/root/pleasehelp/sc_trans sc_trans_mrs.conf

I HAVE to do this to run it:
cd /root/pleasehelp
./sc_trans sc_trans_mrs.conf

The application may rely on relative paths from your current directory, or some other assumption that does not match your situation. Not much Ubuntu can do about a developer's assumptions. Have you asked the developer for support?


> **nitrosrt10 said:**
> 
```

pre-start script
    cd /root/shoutclient
end script

exec ./sc_trans sc_trans_mrs.conf

```

I think you misunderstand the difference between the script stanza and the exec stanza.
Try:
```

script
    cd /root/shoutclient
    ./sc_trans sc_trans_mrs.conf
end script

```

---

