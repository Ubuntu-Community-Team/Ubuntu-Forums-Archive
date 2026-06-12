---
title: "copy user profile"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by merrymarcella on 2008-04-28
Currently i am setting up ubuntu hardy on a second computer. To save time i like to copy the user preferences from thunderbird firefox and openoffice. Some friend suggested that i could just  copy  the .mozilla .mozilla-thunderbird and .openoffice.org2 files from the home directory to the the new home directory. He mentioned that i should get the permissions right and told me how to do this. He said this should work but never tried  himself. So before i ruin things i want to make sure: Will this work?

And when i would install xubuntu on an old laptop laying around, can i do this as well? Or can you do this only between ubuntu installs.

---

### Post by southernman on 2008-04-28
> He said this should work but never tried himself. So before i ruin things i want to make sure: Will this work?Yes

> And when i would install xubuntu on an old laptop laying around, can i do this as well?Makes no difference. You are only transferring a profile folder, that would keep things setup the way you had them on the originating box... for those specific programs.

---

### Post by merrymarcella on 2008-04-28
Thanks for the quick answer!

---

### Post by hyper_ch on 2008-04-28
you'll need to change the ownership to the new user.

```

sudo chown -R NEWUSER.NEWUSER .mozilla

```

---

### Post by southernman on 2008-04-28
> **merrymarcella said:**
> Thanks for the quick answer!
Sure thing! :)

---

