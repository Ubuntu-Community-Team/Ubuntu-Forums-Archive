---
title: "unity"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-05-29
Again I am giving unity a try but when I do all programs and windows have no max, min, close buttons.So I have to log out to get anything to close. I have it set to show all buttons. Also there is no dash at all though I have it set to always show. Also if I try xubuntu orca onboard opens at login but I don't have it in startup applications.

---

### Post by sffvba[e0rt on 2012-05-29
Which version are you trying? Does the windows have borders so you can move them around or are those also missing?


404

---

### Post by cmcanulty on 2012-05-30
I am using 12.04 and tried both 2D and normal unity

---

### Post by raja.genupula on 2012-05-30
have you tried 
```
unity --reset
```  ?

if not press ctrl+alt+F1 and type that one in the terminal .

one more thing is what kind of VGA Drivers you got ? 
```
  lspci -nn | grep VGA
```

---

### Post by cmcanulty on 2012-05-30
the ctrl+alt+f1 took me to a black text login. I have tried reset unity to no effect. I thought it was possible to have gnome classic and still be able logout and into  unity but apparently not which will eliminate me from ever switching to unity

```
cmcanulty@Darcy25:~$  lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
cmcanulty@Darcy25:~$
```

---

### Post by traditionalist on 2012-05-30
> **cmcanulty said:**
> the ctrl+alt+f1 took me to a black text login. I have tried reset unity to no effect. I thought it was possible to have gnome classic and still be able logot and into  unity but apparently not which will eliminate me from ever switching to unity

```
cmcanulty@Darcy25:~$  lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
cmcanulty@Darcy25:~$
```

For some reason my machines will not run both, just causes errors. I removed unity altogether and now have no problems in Gnome Classic either.

---

### Post by Paqman on 2012-05-30
Oops sorry,posted in wrong thread.

---

