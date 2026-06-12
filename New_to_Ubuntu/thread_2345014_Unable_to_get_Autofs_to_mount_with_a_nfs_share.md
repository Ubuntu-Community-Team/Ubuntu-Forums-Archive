---
title: "Unable to get Autofs to mount with a nfs share"
date: 2016-11-29
forum: New to Ubuntu
---

### Post by l2thet on 2016-11-29
There has to be something missing, I can manually mount a nfs share with no issues, for example this works

```
sudo mount 192.168.1.86:/volume1/video /nfs/video/
```

When I try to use Autofs to perform the same steps the /nfs folder is empty. I used this [help how to]("https://help.ubuntu.com/community/Autofs") from this site. Here are the files I have manipulated.

auto.master
```
/nfs      /etc/auto.nfs
```

auto.nfs
```
video      192.168.1.86:/volume1/video
```

It seems like it is only running auto.master and not auto.nfs, when I use the troubleshooting steps from the tutorial I only get the basic startup message when I start the service manually, the attempt to run 'ls' on /nfs does not cause a response.
```
mounted indirect on /nfs with timeout 300, freq 75 seconds
```

After I start autofs /nfs becomes an empty folder, if I stop autofs my original mount returns. I can't help but think it's something I am just not seeing that should be in plain sight.

---

### Post by papibe on 2016-11-29
Hi l2thet.

A few thoughts:

Don't let the partition mounted before starting autofs. Make sure there's nothing mounted there (/nfs).

Make sure you /etc/auto.nfs does not have execute permissions. If it does, automount would assume it is a script. If needed, remove executing permissions like this:
```
sudo chmod a-x /etc/auto.nfs
```

Check if you are using NFS ver3, or ver4:
```
sudo mount -v 192.168.1.86:/volume1/video /nfs/video/
```
(don't forget to unmount),

If you are using ver4, set that up explicitly on auto.nfs:
```
video  -fstype=nfs4      192.168.1.86:/volume1/video
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by l2thet on 2016-11-29
Hi papibe,
  Thank you for the feedback! As requested I checked the things you asked me to look at. At first my results weren't looking good, nfs was ver4, auto.nfs was not executable, and I did a umount on the share before trying again. I couldn't verify that there were only floating mounts from any other attempt, so I performed a reboot... and everything just worked after that! I guess I mucked it up trying so many different things and must have left a mount hanging. Thank you for the feedback and leading me down a path that led to resolution!

---

