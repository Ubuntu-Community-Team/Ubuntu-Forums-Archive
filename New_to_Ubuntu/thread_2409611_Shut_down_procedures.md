---
title: "Shut down procedures"
date: 2019-01-04
forum: New to Ubuntu
---

### Post by BeauteousBlooms on 2019-01-04
From what i can tell, unlike windows, which shuts down all applications appropriately and eject all drives and then shut down the system, ubuntu kinda force kills all applications and 'powers off' the drives attached, i know this because chrome shows the restore box every time i restart, and a click sound from my harddisk (which normally is only heard when the drive is forcefully unplugged) can be heard. I would like to think im wrong and there is an proper way of shutting down the OS, but i dont know. so could people tell me what ubuntu does upon a restart command , e.g how the applications are closed down, how storage mediums are disconnected, that would be much appropriated.

---

### Post by Impavidus on 2019-01-04
Let me try this. I'm not really a specialist on this subject.

When you shutdown, a signal is sent to all running processes. When its parent process terminates it may get the SIGHUP signal, but ultimately it's guaranteed that every process still running when the system shuts down receives the SIGTERM signal, which is a kind request to terminate the process ASAP. The application may be designed to handle this signal and quickly save some files, but even then it may be considered abnormal termination and cause some restore thing the next time it's started. Processes not responding to this kind request will get the SIGKILL signal a few seconds later, leading to immediate termination of the program. This way of terminating the process is different from clicking File&#8594;Exit, which is entirely handled by the application itself, or from clicking that X-symbol, which causes the window manager to send a signal to the application, informing it that the user has clicked on that X. Next all pending writes to storage media are flushed, filesystems are remounted read-only and the system powers off or restarts. The difference with Windows is that Windows likes to use some kind of hibernation that doesn't cleanly unmount the filesystems.

I don't use chrome. The code for handling termination of chrome when the system shuts down must be different on UNIX-like systems compared to Windows, therefore it may behave differently. I think that the spinning hard drives are supposed to have their read heads retracted and spin down before power is cut, but on a previous Ubuntu release I noticed that that didn't always work on my laptop. Hard drives are mechanically designed in such a way that that shouldn't cause damage.

---

