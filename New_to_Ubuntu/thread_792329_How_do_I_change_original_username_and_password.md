---
title: "How do I change original username and password?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-05-12
Hello all,

I have a dual-boot XP-Hardy  machine. How do I change the initial username and password, i.e. those that were setup when I first install Ununtu?

Thanks a lot for your help.

---

### Post by jnorth on 2008-05-12
> **iClouseau88 said:**
> Hello all,

I have a dual-boot XP-Hardy  machine. How do I change the initial username and password, i.e. those that were setup when I first install Ununtu?

Thanks a lot for your help.

IMHO it'd be easier to just create a new user, copy any files that you need over, and delete the old.  But that's just my opinion.

The reason I wouldn't just copy your home directory as is to a new user is that a lot of your applications have username-specific data stored in them and could(will) cause some very odd behavior.

Just make sure that if you add a new user and go that route that you add the new user to all the same groups that your original username was part of, or you could find yourself with a more involved operation of getting your sudo privileges back - doable but more involved.

Use the System/Administration/Users & Groups tool to manage your users FYI.

---

### Post by aysiu on 2008-05-12
Try this:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Or just add a new user.

---

### Post by jnorth on 2008-05-12
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Or just add a new user.

Yeah, I didn't consider the possibility when I wrote that that maybe they just lost the password or want to change it :)  If that's the case then by all means just change the password, far easier and cleaner.  If you still want to change the username too though, you're going to have to create the new user.  I just assumed (yeah I know what that means :)) that you wanted to rename the user for some reason (marriage, death, new significant other, selling, giving away, whatever)

LOL @aysiu - I've been trying to spend more time on here giving back to the community but my post count is kinda pitiful compared to yours!

---

### Post by spiderbatdad on 2008-05-12
supposedly the username can be changed with usermod and then the user id, as well, so the new username inherits the files of the old user name: [http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

---

### Post by jnorth on 2008-05-12
> **spiderbatdad said:**
> supposedly the username can be changed with usermod and then the user id, as well, so the new username inherits the files of the old user name: [http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

Yeah but you still gotta deal with all the other files and settings in there for gnome and such... not that it can't be done it could just be difficult.

---

### Post by spiderbatdad on 2008-05-13
> **jnorth said:**
> Yeah but you still gotta deal with all the other files and settings in there for gnome and such... not that it can't be done it could just be difficult.

I believe your caution and word of warning are well justified. I have not rushed to test the on my working account...nor do I think I will.

---

