---
title: "Grep and date filtering"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by giasone777 on 2012-08-20
I found this command on the internet 
 
**[SIZE=3][FONT=Calibri]cat /var/log/mail.log |grep "status=sent" |grep -E 'Aug 14 (1[0-1]:[0-5][0-9]|12:00)'[/FONT][/SIZE]**
**[SIZE=3][FONT=Calibri][/FONT][/SIZE]** 
**[SIZE=3][FONT=Calibri]Which looks up all  instances where status= sent within the postfix mail.log between the time of 10 and 12pm on Aug 14[/FONT][/SIZE]**
**[FONT=Calibri][SIZE=3][/SIZE][/FONT]** 
**[FONT=Calibri][SIZE=3]The date part is obvious, but I don't understand how the time section works, could somebody please give me a detailed explaination of how the time is filtered between 10 and 12.[/SIZE][/FONT]**
[B][FONT=Calibri][SIZE=3]
Thank-you![/SIZE][/FONT][/B]

---

### Post by SeijiSensei on 2012-08-20
The construct [0-5] matches all values between zero and five.  So [0-5][0-9] will matching anything from 00 to 59. The first part of the regex before the vertical bar thus matches any string that starts with a one, followed by either a zero or a one, followed by a colon, followed by 00-59.  The vertical bar is an "or" condition which only works when you run grep in "extended" mode using the -E switch.  So the entire expression will match any time from 10:00 to 11:59 or specifically the time 12:00.

---

