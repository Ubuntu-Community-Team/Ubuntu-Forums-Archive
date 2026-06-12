---
title: "how can I kill a program at a specified time?"
date: 2016-05-23
forum: Programming Talk
---

### Post by sam_baker2 on 2016-05-23
hello, I want to be able to kill a program at a specified time. I don't want to set up the cron tab, I just want a simple command to type into the terminal.  Example: I want to kill Firefox, say, in 2 hours and 10 minutes, how would I do that? I think it involves the "at" and "kill" command, but don't know how to word it. Thanks for any info.

---

### Post by ajgreeny on 2016-05-23
You could do it with a simple sleep addition to the kill command eg ```
sleep 60m; killall *application*
```Just change the sleep length and application to fit your situation.

I used to do this in the past to record online radio streams, eg
```
/usr/bin/mplayer -cache 2048 -playlist stream-URL -vc null -vo null -ao pcm:fast:waveheader:file=filename.wav & sleep 60m; killall mplayer
```

---

### Post by steeldriver on 2016-05-23
Something like

```

echo 'pkill firefox' | at now + 130 minutes

```

should work, I think

---

### Post by sam_baker2 on 2016-05-23
ok, thanks

---

