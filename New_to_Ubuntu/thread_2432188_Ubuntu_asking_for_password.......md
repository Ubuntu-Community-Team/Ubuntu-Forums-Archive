---
title: "Ubuntu asking for password......"
date: 2019-11-28
forum: New to Ubuntu
---

### Post by chris-burmajster on 2019-11-28
Hello,

I have a problem. Ubuntu 19.10 is asking for a password. I input the correct password and it does not work. What am I doing wrong? I can't get into the OS because of the password.

Chris

---

### Post by Impavidus on 2019-11-28
Does it say you used an incorrect password or does login simply fail?

---

### Post by crip720 on 2019-11-28
I found that with 19.10 it has started to ask for user name first then the password.  Try inputting your user name in first box the the second box should accept your password.  This is for the login page, if it is for different page or program, please let us know.

---

### Post by chris-burmajster on 2019-11-28
No, it's for the login page. I tried inputting my first name, and then the password, but it just goes back to the beginning. And login simply fails.

---

### Post by chris-burmajster on 2019-11-28
I used the correct password and then it simply fails. I tried inputting my name in first, then the password, but it does not work.

---

### Post by crip720 on 2019-11-28
It has to be user name.  Is your first name the user name?  It is user name hit enter, then password and hit enter.  I imagine this is what you are doing, just making sure.  Also make sure 'Caps Lock' is off.

---

### Post by chris-burmajster on 2019-11-28
User name is chris. I have tried inputting with uppercase and lowercase C but it does not make any difference. I'm certain caps lock is off because I can set the password to see it as I type.

---

### Post by crip720 on 2019-11-28
If positive you are putting in right user and password, then something is wonky.  You did not mention if it was an upgrade or clean install.  You can google for changing lost password in ubuntu, will need a Live version on usb stick, or if it is recent and no data on it, might just be easier to reinstall, remembering to write down user name and password.

---

### Post by deadflowr on 2019-11-28
> I used the correct password and then it simply fails. I tried inputting my name in first, then the password, but it does not work.
So no Incorrect password statement?
Just resets itself?

In that case try setting a different session.

If we are talking Ubuntu then after name selection when the password field appears,
next to the sign in button should show a cog icon, 
click on that and see which Desktop sessions are available and try to select one.

---

### Post by chris-burmajster on 2019-11-28
It's a clean install. It gives me the incorrect password statement sometimes or re-sets itself. There is no cog icon, except when it's rotating whilst working out the password. I'm sorry, I've had two strokes and my english isn't perfect.

---

### Post by crip720 on 2019-11-28
The cog icon should be to be top right of box and might look more like a round circle.

---

### Post by oldrocker99 on 2019-11-28
The simplest solution would simply be to reinstall. It'll take far less time than finding the wonky problem that you have's solution.

---

### Post by chris-burmajster on 2019-11-29
Well, for the second time in 5 days I wiped the computer and restord from backup.

---

### Post by Impavidus on 2019-11-29
When it fails to login, you often have a permissions issue. Maybe some file in your home directory didn't have the right owner or permissions. Owner is simple: All files in your home directory should be owned by you. If you use ctrl+alt+F2 to login to a terminal session, it may be possible to fix this. This may result from incorrect use of sudo.

Just so you know it for next time.

---

