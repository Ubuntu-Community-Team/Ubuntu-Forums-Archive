---
title: "my firefox can't open and now apt, apt-get and aptitude are also broken"
date: 2017-09-08
forum: New to Ubuntu
---

### Post by luiz-felipe.bjc on 2017-09-08
I have ubuntu 17.04 every time I open firefox it crashes, when opened by the terminal it gave the following error message:
ExceptionHandler :: GenerateDump cloned child 2491
ExceptionHandler :: SendContinueSignalToChild sent continue signal to child
ExceptionHandler :: WaitForContinueSignal waiting for continue signal ...
Bus error (recorded core image)
I had even tried to uninstall firefox and reinstall, but continued with the problem, I also tried deleting the ~ / .mozilla / firefox / directory and doing the same, then the whole ~ / .mozilla/ directory, but it also didn't solve the  problem.
Until yesterday the installers (apt, apt-get, aptitude) worked, but now they are also giving bus error, do you know how can I solve it?

---

### Post by wildmanne39 on 2017-09-08
*Thread moved to **New to Ubuntu**.*

Please use English, you can translate with google if needed. This is an English only forum you posted in.

Please do not post help threads in the Resolution Center.

Thanks

---

### Post by luiz-felipe.bjc on 2017-09-08
ok, I will use english from now

---

### Post by luiz-felipe.bjc on 2017-09-08
I've editted the post because I initially posted in portuguese and I used a internet slang abbreviation for "when" which wasn't translated and I think it's clearer now

---

### Post by luiz-felipe.bjc on 2017-09-09
I just changed the network mirror and solved the problem with apt, apt-get and aptitude even changing again to the same I was using before it works normally, but I still have the problem with firefox even purging and installing again and even removing ~/.mozilla and doing it, I think it may give an idea of the cause of the problem but I still don't know, may you help me please to solve the problem with firefox?

---

