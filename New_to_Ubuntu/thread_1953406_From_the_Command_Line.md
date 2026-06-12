---
title: "From the Command Line"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by Old-un on 2012-04-06
Can anyone tell me how i might find out from the command line if i have previously installed for example: ffmpeg or youtube-dl. Thanks

---

### Post by nothingspecial on 2012-04-06
You can try ```
history
``` to see your most recent commands.

Another method would be to do 

```
grep "ffmpeg" /var/log/apt/history.log
```

and

```
zgrep --colour "ffmpeg" /var/log/apt/history.log.1.gz
```

repeating the zgrep on any other apt history gzipped logs

---

### Post by athampan on 2012-04-06
```
sudo updatedb; locate <softwarename>
```

---

### Post by Toz on 2012-04-06
You can also use apt-cache:
```
apt-cache policy youtube-dl
```

---

### Post by Old-un on 2012-04-06
Thanks for all the help everyone!

---

### Post by lukeiamyourfather on 2012-04-06
Another good one is which.

```

which ffmpeg

```

If ffmpeg is found in the path it will show where.

---

