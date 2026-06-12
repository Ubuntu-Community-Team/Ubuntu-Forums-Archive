---
title: "Diff files etc"
date: 2016-03-11
forum: New to Ubuntu
---

### Post by jon80 on 2016-03-11
How do I open .diff files and what do I do with them please?  
Are they something to do with the unix diff tool, the one that checks for differences between files?

Also I got an ftp connection refused error when I tried connecting from my virtual machine to the guest machine.  The guest machine runs FileZilla FileServer and the virtual machine runs Oracle VirtualBox.  Network connection uses wireless which is intermittently going off sometimes and causing me to reconnect.

```
jon@unix-box:~$ .f-spot-0.8.0-0.8.1.diff
.f-spot-0.8.0-0.8.1.diff: command not found
jon@unix-box:~$ ./f-spot-0.8.0-0.8.1.diff
bash: ./f-spot-0.8.0-0.8.1.diff: Permission denied
jon@unix-box:~$ chmod +755 f-spot-0.8.0-0.8.1.diff
jon@unix-box:~$ ./f-spot-0.8.0-0.8.1.diff
diff: f-spot-0.8.0/aclocal.m4: No such file or directory
diff: f-spot-0.8.1/aclocal.m4: No such file or directory
./f-spot-0.8.0-0.8.1.diff: line 2: ---: command not found
./f-spot-0.8.0-0.8.1.diff: line 3: +++: command not found
./f-spot-0.8.0-0.8.1.diff: line 4: @@: command not found
./f-spot-0.8.0-0.8.1.diff: line 7: syntax error near unexpected token `[build/m4/shave/shave.m4]'
./f-spot-0.8.0-0.8.1.diff: line 7: ` m4_include([build/m4/shave/shave.m4])'
jon@unix-box:~$

**log**
--
(000559) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000559) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000559) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000559) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000560) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000560) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000560) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000560) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000559) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> disconnected.
(000560) 20/07/2014 11:12:43 - (not logged in) (127.0.0.1)> disconnected.
(000561) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000561) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000561) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000561) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000562) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000562) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000562) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000562) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000561) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> disconnected.
(000562) 20/07/2014 11:18:43 - (not logged in) (127.0.0.1)> disconnected.
(000563) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000563) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000563) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000563) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000564) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000564) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000564) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000564) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000563) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> disconnected.
(000564) 20/07/2014 11:24:43 - (not logged in) (127.0.0.1)> disconnected.
(000565) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000565) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000565) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000565) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000566) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000566) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000566) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000566) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000566) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000565) 20/07/2014 11:30:43 - (not logged in) (127.0.0.1)> disconnected.
(000567) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000567) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000567) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000567) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000568) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000568) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000568) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000568) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000567) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> disconnected.
(000568) 20/07/2014 11:36:43 - (not logged in) (127.0.0.1)> disconnected.
(000569) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000569) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000569) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000569) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000570) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000570) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000570) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000570) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000570) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000569) 20/07/2014 11:42:43 - (not logged in) (127.0.0.1)> disconnected.
(000571) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000571) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000571) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000571) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000571) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000572) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000572) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000572) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000572) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000572) 20/07/2014 11:48:44 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000573) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000573) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000573) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000573) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000573) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> disconnected.
(000574) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000574) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000574) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000574) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000574) 20/07/2014 12:01:18 - (not logged in) (127.0.0.1)> disconnected.
(000575) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000575) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000575) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000575) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000575) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000576) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000576) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000576) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000576) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000576) 20/07/2014 12:07:18 - (not logged in) (127.0.0.1)> disconnected.
(000577) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000577) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000577) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000577) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000578) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000578) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000578) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000578) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000578) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000577) 20/07/2014 12:13:18 - (not logged in) (127.0.0.1)> disconnected.
(000579) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000579) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000579) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000579) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000579) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000580) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000580) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000580) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000580) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000580) 20/07/2014 12:19:18 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000581) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000581) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000581) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000581) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000582) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000582) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000582) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000582) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000581) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> disconnected.
(000582) 20/07/2014 12:25:18 - (not logged in) (127.0.0.1)> disconnected.
(000583) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000583) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000583) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000583) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000584) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000584) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000584) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000584) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000583) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> disconnected.
(000584) 20/07/2014 12:31:19 - (not logged in) (127.0.0.1)> disconnected.
(000585) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000585) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000585) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000585) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000586) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000586) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000586) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000586) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000585) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> disconnected.
(000586) 20/07/2014 12:37:19 - (not logged in) (127.0.0.1)> disconnected.
(000587) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000587) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000587) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000587) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000587) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000588) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000588) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000588) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000588) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000588) 20/07/2014 12:43:19 - (not logged in) (127.0.0.1)> disconnected.
(000589) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000589) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000589) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000589) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000590) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000590) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000590) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000590) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000589) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> disconnected.
(000590) 20/07/2014 12:49:19 - (not logged in) (127.0.0.1)> disconnected.
(000591) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000591) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000591) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000591) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000592) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000592) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000592) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000592) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000592) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000591) 20/07/2014 12:55:19 - (not logged in) (127.0.0.1)> disconnected.
(000593) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000593) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000593) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000593) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000593) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000594) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000594) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000594) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000594) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000594) 20/07/2014 13:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000595) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000595) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000595) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000596) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000596) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000595) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000596) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000596) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000595) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> disconnected.
(000596) 20/07/2014 13:07:19 - (not logged in) (127.0.0.1)> disconnected.
(000597) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000597) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000597) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000597) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000597) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000598) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000598) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000598) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000598) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000598) 20/07/2014 13:13:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000599) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000599) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000599) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000599) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000599) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000600) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000600) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000600) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000600) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000600) 20/07/2014 13:19:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000601) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000601) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000601) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000601) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000602) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000602) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000602) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000602) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000602) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000601) 20/07/2014 13:25:19 - (not logged in) (127.0.0.1)> disconnected.
(000603) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000603) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000603) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000603) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000603) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000604) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000604) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000604) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000604) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000604) 20/07/2014 13:31:19 - (not logged in) (127.0.0.1)> disconnected.
(000605) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000605) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000605) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000605) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000605) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000606) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000606) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000606) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000606) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000606) 20/07/2014 13:37:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000607) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000607) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000607) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000607) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000607) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000608) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000608) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000608) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000608) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000608) 20/07/2014 13:43:19 - (not logged in) (127.0.0.1)> disconnected.
(000609) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000609) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000609) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000609) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000609) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000610) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000610) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000610) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000610) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000610) 20/07/2014 13:49:19 - (not logged in) (127.0.0.1)> disconnected.
(000611) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000611) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000611) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000611) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000611) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000612) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000612) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000612) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000612) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000612) 20/07/2014 13:55:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000613) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000613) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000613) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000613) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000613) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000614) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000614) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000614) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000614) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000614) 20/07/2014 14:01:19 - (not logged in) (127.0.0.1)> disconnected.
(000615) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000615) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000615) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000615) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000615) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000616) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000616) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000616) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000616) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000616) 20/07/2014 14:07:19 - (not logged in) (127.0.0.1)> disconnected.
(000617) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000617) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000617) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000617) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000617) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000618) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000618) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000618) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000618) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000618) 20/07/2014 14:13:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000619) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000619) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000619) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000619) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000619) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000620) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000620) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000620) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000620) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000620) 20/07/2014 14:19:19 - (not logged in) (127.0.0.1)> disconnected.
(000621) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000621) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000621) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000621) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000622) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000622) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000622) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000622) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000621) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> disconnected.
(000622) 20/07/2014 14:25:19 - (not logged in) (127.0.0.1)> disconnected.
(000623) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000623) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000623) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000623) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000623) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000624) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000624) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000624) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000624) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000624) 20/07/2014 14:31:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000625) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000625) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000625) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000625) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000625) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000626) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000626) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000626) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000626) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000626) 20/07/2014 14:37:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000627) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000627) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000627) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000627) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000627) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000628) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000628) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000628) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000628) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000628) 20/07/2014 14:43:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000629) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000629) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000629) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000629) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000629) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000630) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000630) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000630) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000630) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000630) 20/07/2014 14:49:19 - (not logged in) (127.0.0.1)> disconnected.
(000631) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000631) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000631) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000631) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000631) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000632) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000632) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000632) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000632) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000632) 20/07/2014 14:55:19 - (not logged in) (127.0.0.1)> disconnected.
(000633) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000633) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000633) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000633) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000633) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000634) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000634) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000634) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000634) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000634) 20/07/2014 15:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000635) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000635) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000635) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000635) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000635) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000636) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000636) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000636) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000636) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000636) 20/07/2014 15:07:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000637) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000637) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000637) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000637) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000637) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> disconnected.
(000638) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000638) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000638) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000638) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000638) 20/07/2014 15:13:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000639) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000639) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000639) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000639) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000639) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000640) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000640) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000640) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000640) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000640) 20/07/2014 15:19:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000641) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000641) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000641) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000641) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000641) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000642) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000642) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000642) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000642) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000642) 20/07/2014 15:25:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000643) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000643) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000643) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000643) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000643) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000644) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000644) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000644) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000644) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000644) 20/07/2014 15:31:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000645) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000645) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000645) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000645) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000645) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000646) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000646) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000646) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000646) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000646) 20/07/2014 15:37:19 - (not logged in) (127.0.0.1)> disconnected.
(000647) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000647) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000647) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000647) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000647) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000648) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000648) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000648) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000648) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000648) 20/07/2014 15:43:19 - (not logged in) (127.0.0.1)> disconnected.
(000649) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000649) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000649) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000649) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000650) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000650) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000650) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000650) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000650) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000649) 20/07/2014 15:49:19 - (not logged in) (127.0.0.1)> disconnected.
(000651) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000651) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000651) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000651) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000651) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000652) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000652) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000652) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000652) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000652) 20/07/2014 15:55:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000653) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000653) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000653) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000653) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000653) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000654) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000654) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000654) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000654) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000654) 20/07/2014 16:01:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000655) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000655) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000655) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000655) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000655) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000656) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000656) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000656) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000656) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000656) 20/07/2014 16:07:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000657) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000657) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000657) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000657) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000657) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000658) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000658) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000658) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000658) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000658) 20/07/2014 16:13:19 - (not logged in) (127.0.0.1)> disconnected.
(000659) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000659) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000659) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000660) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000660) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000659) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000660) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000660) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000659) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> disconnected.
(000660) 20/07/2014 16:19:19 - (not logged in) (127.0.0.1)> disconnected.
(000661) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000661) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000661) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000661) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000661) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000662) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000662) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000662) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000662) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000662) 20/07/2014 16:25:19 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000663) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000663) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000663) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000663) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000663) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000664) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000664) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000664) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000664) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000664) 20/07/2014 16:31:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000665) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000665) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000665) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000665) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000665) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000666) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000666) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000666) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000666) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000666) 20/07/2014 16:37:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000667) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000667) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000667) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000667) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000667) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000668) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000668) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000668) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000668) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000668) 20/07/2014 16:43:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000669) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000669) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000669) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000669) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000669) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000670) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000670) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000670) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000670) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000670) 20/07/2014 16:49:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000671) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000671) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000671) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000671) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000671) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000672) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000672) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000672) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000672) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000672) 20/07/2014 16:55:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000673) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000673) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000673) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000673) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000674) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000674) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000674) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000674) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000673) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> disconnected.
(000674) 20/07/2014 17:01:20 - (not logged in) (127.0.0.1)> disconnected.
(000675) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000675) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000675) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000675) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000675) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000676) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000676) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000676) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000676) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000676) 20/07/2014 17:07:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000677) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000677) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000677) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000677) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000677) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000678) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000678) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000678) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000678) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000678) 20/07/2014 17:13:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000679) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000679) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000679) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000679) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000679) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000680) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000680) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000680) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000680) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000680) 20/07/2014 17:19:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000681) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000681) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000681) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000681) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000681) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000682) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000682) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000682) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000682) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000682) 20/07/2014 17:25:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000683) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000683) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000683) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000683) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000683) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000684) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000684) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000684) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000684) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000684) 20/07/2014 17:31:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000685) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000685) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000685) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000685) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000685) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000686) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000686) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000686) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000686) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000686) 20/07/2014 17:37:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000687) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000687) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000687) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000687) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000687) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000688) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000688) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000688) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000688) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000688) 20/07/2014 17:43:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000689) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000689) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000689) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000689) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000689) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000690) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000690) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000690) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000690) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000690) 20/07/2014 17:49:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000691) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000691) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000691) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000691) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000691) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000692) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000692) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000692) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000692) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000692) 20/07/2014 17:55:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000693) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000693) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000693) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000693) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000693) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> disconnected.
(000694) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000694) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000694) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000694) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000694) 20/07/2014 18:01:20 - (not logged in) (127.0.0.1)> disconnected.
(000695) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000695) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000695) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000695) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000695) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000696) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000696) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000696) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000696) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000696) 20/07/2014 18:07:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000697) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000697) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000697) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000697) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000697) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000698) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000698) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000698) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000698) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000698) 20/07/2014 18:13:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000699) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000699) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000699) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000699) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000699) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000700) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000700) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000700) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000700) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000700) 20/07/2014 18:19:20 - (not logged in) (127.0.0.1)> disconnected.
(000701) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000701) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000701) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000701) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000701) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000702) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000702) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000702) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000702) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000702) 20/07/2014 18:25:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000703) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000703) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000703) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000703) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000703) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000704) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000704) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000704) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000704) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000704) 20/07/2014 18:31:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000705) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000705) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000705) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000705) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000705) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000706) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000706) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000706) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000706) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000706) 20/07/2014 18:37:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000707) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000707) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000707) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000707) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000707) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000708) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000708) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000708) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000708) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000708) 20/07/2014 18:43:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000709) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000709) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000709) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000709) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000709) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000710) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000710) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000710) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000710) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000710) 20/07/2014 18:49:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000711) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000711) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000711) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000711) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000711) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000712) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000712) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000712) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000712) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000712) 20/07/2014 18:55:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000713) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000713) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000713) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000713) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000713) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000714) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000714) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000714) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000714) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000714) 20/07/2014 19:01:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000715) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000715) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000715) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000715) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000715) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000716) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000716) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000716) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000716) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000716) 20/07/2014 19:07:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000717) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000717) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000717) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000717) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000717) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000718) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000718) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000718) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000718) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000718) 20/07/2014 19:13:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000719) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000719) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000719) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000719) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000719) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000720) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000720) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000720) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000720) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000720) 20/07/2014 19:19:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000721) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000721) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000721) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000721) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000721) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000722) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000722) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000722) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000722) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000722) 20/07/2014 19:25:20 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000723) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000723) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000723) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000723) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000723) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> disconnected.
(000724) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000724) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000724) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000724) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000724) 20/07/2014 22:25:48 - (not logged in) (127.0.0.1)> disconnected.
(000725) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000725) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000725) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000725) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000726) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000726) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000725) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> disconnected.
(000726) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000726) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000726) 21/07/2014 08:55:16 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000727) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000727) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000727) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000727) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000728) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000728) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000728) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000728) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000727) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> disconnected.
(000728) 21/07/2014 09:01:16 - (not logged in) (127.0.0.1)> disconnected.
(000729) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000729) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000729) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000729) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000729) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000730) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000730) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000730) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000730) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000730) 21/07/2014 09:07:16 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
FileZilla Server version 0.9.44 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
(000001) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000001) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000001) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000001) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000001) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000002) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000002) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000002) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000002) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000002) 21/07/2014 09:11:36 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000003) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000003) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000003) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000003) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000003) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000004) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000004) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000004) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000004) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000004) 21/07/2014 09:17:36 - (not logged in) (127.0.0.1)> disconnected.
Server offline.
FileZilla Server version 0.9.44 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
(000001) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000001) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000001) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000001) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000001) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000002) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000002) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000002) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000002) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000002) 21/07/2014 09:23:10 - (not logged in) (127.0.0.1)> disconnected.
(000003) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000003) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000003) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000003) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000004) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000004) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000004) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000004) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000003) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> disconnected.
(000004) 21/07/2014 09:29:10 - (not logged in) (127.0.0.1)> disconnected.
(000005) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000005) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000005) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000005) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000005) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000006) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000006) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000006) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000006) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000006) 21/07/2014 09:35:10 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000007) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000007) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000007) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000007) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000007) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
(000008) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> Connected, sending welcome message...
(000008) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> 220-FileZilla Server version 0.9.44 beta
(000008) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000008) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> 220 Please visit [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)
(000008) 21/07/2014 09:41:10 - (not logged in) (127.0.0.1)> could not send reply, disconnected.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
Server offline.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
FileZilla Server 0.9.53 beta started
Initializing Server.
Creating listen socket on port 21...
Server online.
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
(000001) 10/03/2016 20:22:53 - (not logged in) (192.168.0.14)> Connected on port 21, sending welcome message...
(000001) 10/03/2016 20:22:53 - (not logged in) (192.168.0.14)> 220-FileZilla Server 0.9.53 beta
(000001) 10/03/2016 20:22:53 - (not logged in) (192.168.0.14)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000001) 10/03/2016 20:22:53 - (not logged in) (192.168.0.14)> 220 Please visit [https://filezilla-project.org/](https://filezilla-project.org/)
(000001) 10/03/2016 20:22:56 - (not logged in) (192.168.0.14)> USER jon
(000001) 10/03/2016 20:22:56 - (not logged in) (192.168.0.14)> 331 Password required for jon
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
(000001) 10/03/2016 20:23:54 - (not logged in) (192.168.0.14)> 421 Login time exceeded. Closing control connection.
(000001) 10/03/2016 20:23:54 - (not logged in) (192.168.0.14)> disconnected.
(000002) 10/03/2016 20:24:50 - (not logged in) (192.168.0.14)> Connected on port 21, sending welcome message...
(000002) 10/03/2016 20:24:50 - (not logged in) (192.168.0.14)> 220-FileZilla Server 0.9.53 beta
(000002) 10/03/2016 20:24:50 - (not logged in) (192.168.0.14)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000002) 10/03/2016 20:24:50 - (not logged in) (192.168.0.14)> 220 Please visit [https://filezilla-project.org/](https://filezilla-project.org/)
(000002) 10/03/2016 20:24:52 - (not logged in) (192.168.0.14)> USER jon
(000002) 10/03/2016 20:24:52 - (not logged in) (192.168.0.14)> 331 Password required for jon
(000002) 10/03/2016 20:24:54 - (not logged in) (192.168.0.14)> PASS *********
(000002) 10/03/2016 20:24:54 - jon (192.168.0.14)> 230 Logged on
(000002) 10/03/2016 20:24:54 - jon (192.168.0.14)> SYST
(000002) 10/03/2016 20:24:54 - jon (192.168.0.14)> 215 UNIX emulated by FileZilla
(000002) 10/03/2016 20:25:33 - jon (192.168.0.14)> PORT 10,0,2,15,201,189
(000002) 10/03/2016 20:25:33 - jon (192.168.0.14)> 421 Rejected command, requested IP address does not match control connection IP.
(000002) 10/03/2016 20:25:33 - jon (192.168.0.14)> disconnected.
(000003) 10/03/2016 20:27:18 - (not logged in) (192.168.0.14)> Connected on port 21, sending welcome message...
(000003) 10/03/2016 20:27:18 - (not logged in) (192.168.0.14)> 220-FileZilla Server 0.9.53 beta
(000003) 10/03/2016 20:27:18 - (not logged in) (192.168.0.14)> 220-written by Tim Kosse (tim.kosse@filezilla-project.org)
(000003) 10/03/2016 20:27:18 - (not logged in) (192.168.0.14)> 220 Please visit [https://filezilla-project.org/](https://filezilla-project.org/)
(000003) 10/03/2016 20:27:20 - (not logged in) (192.168.0.14)> USER jon
(000003) 10/03/2016 20:27:20 - (not logged in) (192.168.0.14)> 331 Password required for jon
(000003) 10/03/2016 20:27:22 - (not logged in) (192.168.0.14)> PASS *********
(000003) 10/03/2016 20:27:22 - jon (192.168.0.14)> 230 Logged on
(000003) 10/03/2016 20:27:22 - jon (192.168.0.14)> SYST
(000003) 10/03/2016 20:27:22 - jon (192.168.0.14)> 215 UNIX emulated by FileZilla
(000003) 10/03/2016 20:27:30 - jon (192.168.0.14)> PORT 10,0,2,15,150,74
(000003) 10/03/2016 20:27:30 - jon (192.168.0.14)> 421 Rejected command, requested IP address does not match control connection IP.
(000003) 10/03/2016 20:27:30 - jon (192.168.0.14)> disconnected.
Server offline.
Warning: FTP over TLS is not enabled, users cannot securely log in.
Warning: FTP over TLS is not enabled, users cannot securely log in.
Warning: FTP over TLS is not enabled, users cannot securely log in.
Warning: Explicit FTP over TLS is not enabled or there is no FTP listen socket configured.
Warning: Explicit FTP over TLS is not enabled or there is no FTP listen socket configured.
```
The last warning gives a conflicting message as I have configured the appropriate flag within the user interface within FTP Server 0.9.53 beta.  I have updated other software by Filezilla but I am not aware of any newer releases for the ftp server software, perhaps I will try another one, however I am sure it used to work, perhaps this is a regression error within the software, or something of the sort, I am not sure.

---

### Post by TheFu on 2016-03-11
File extensions don't mean the same thing on *nix as they do on Windows.  It is helpful to humans.  The diff manpage can explain more.
[https://linuxacademy.com/blog/linux/introduction-using-diff-and-patch/](https://linuxacademy.com/blog/linux/introduction-using-diff-and-patch/) is a nicer explanation.

Most people shouldn't use plain FTP. It isn't secure and transmits passwords in clear-text, like telnet.  Use **sftp** instead. All file browsers on Linux support sftp:// URLs. Every network OS has support for ssh, scp and sftp.  Being able to securely access your files from anywhere in the world is kinda nice. sftp is installed and working when openssh-server is installed.  Easy.  More convincing?  [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  Be certain to secure the ssh server (which will secure both scp and sftp servers too) and never use/allow passwords for authentication over the internet. ;)

If you need to make files available for anonymous visitors, use HTTP instead.



IMHO.

---

