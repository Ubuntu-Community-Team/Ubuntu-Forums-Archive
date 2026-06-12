---
title: "Help with a sed expression?"
date: 2011-09-20
forum: Programming Talk
---

### Post by nerdopolis on 2011-09-20
Hi.

I am trying to use sed to replace a string only if its NOT near a letter or a number.

So for example I want to change all instances of usr to NEW

I have it where "4usr4" will stay as 4usr4 and %usr% will be %NEW%.

The problem is that it seems it does not replace it if its on the end of the line
"%usr" will stay as "%usr" when (notice the space) "%usr " will be "%NEW " It does seem to work the way I want it to for "usr%" where if its directly on the start of the line.

This is what I have so far
```
sed "/^[^a-zA-Z0-9]*usr[^a-zA-Z0-9]/ s/usr/NEW/g"
```

Anyone have any ideas?

Thanks.

---

### Post by ofnuts on 2011-09-20
> **nerdopolis said:**
> Hi.

I am trying to use sed to replace a string only if its NOT near a letter or a number.

So for example I want to change all instances of usr to NEW

I have it where "4usr4" will stay as 4usr4 and %usr% will be %NEW%.

The problem is that it seems it does not replace it if its on the end of the line
"%usr" will stay as "%usr" when (notice the space) "%usr " will be "%NEW " It does seem to work the way I want it to for "usr%" where if its directly on the start of the line.

This is what I have so far
```
sed "/^[^a-zA-Z0-9]*usr[^a-zA-Z0-9]/ s/usr/NEW/g"
```Anyone have any ideas?

Thanks.[^a-zA-Z0-9]* always matches... This seems to work:

```
sed -re 's/(\W|^)user(\W|$)/\1NEW\2/'
```With:
```
user
1user
user1
1user2
-user
user-
-user-

```gives:
```
NEW
1user
user1
1user2
-NEW
NEW-
-NEW-

```

---

### Post by Arndt on 2011-09-20
> **nerdopolis said:**
> Hi.

I am trying to use sed to replace a string only if its NOT near a letter or a number.

So for example I want to change all instances of usr to NEW

I have it where "4usr4" will stay as 4usr4 and %usr% will be %NEW%.

The problem is that it seems it does not replace it if its on the end of the line
"%usr" will stay as "%usr" when (notice the space) "%usr " will be "%NEW " It does seem to work the way I want it to for "usr%" where if its directly on the start of the line.

This is what I have so far
```
sed "/^[^a-zA-Z0-9]*usr[^a-zA-Z0-9]/ s/usr/NEW/g"
```

Anyone have any ideas?

Thanks.

```
$ echo "%usr% 4usr4" | sed "/^[^a-zA-Z0-9]*usr[^a-zA-Z0-9]/ s/usr/NEW/g"
%NEW% 4NEW4

```

---

### Post by nerdopolis on 2011-09-20
> **ofnuts said:**
> [^a-zA-Z0-9]* always matches... This seems to work:

```
sed -re 's/(\W|^)user(\W|$)/\1NEW\2/'
```With:
```
user
1user
user1
1user2
-user
user-
-user-

```gives:
```
NEW
1user
user1
1user2
-NEW
NEW-
-NEW-

```

Thank you! that seems to work great!

---

### Post by nerdopolis on 2011-10-08
OK that line was deleting the two wild cards so I changed it to
```
sed -re '/(\W|^)usr(\W|$)/ s/usr/NEW/g'
```but then I ran into an issue with a line like this:

```
uusrr usr 
```it does not just replace the second one that I want to be changed because it isn't near word characters,  It replaces BOTH of them, even if it is near word characters because the of the first one!

So in the end I ended up changing it to this
```
sed -re 's/(\W|^)usr(\W|$)/\1NEW\2/g'
```(notice the \1 and \2) and it seems to be working for me!

Just in case if anyone is looking how to do this on Google sometime in 2014 or so and the find this thread

---

### Post by ofnuts on 2011-10-09
> **nerdopolis said:**
> OK that line was deleting the two wild cards so I changed it to
```
sed -re '/(\W|^)usr(\W|$)/ s/usr/NEW/g'
```but then I ran into an issue with a line like this:

```
uusrr usr 
```it does not just replace the second one that I want to be changed because it isn't near word characters,  It replaces BOTH of them, even if it is near word characters because the of the first one!

So in the end I ended up changing it to this
```
sed -re 's/(\W|^)usr(\W|$)/\1NEW\2/g'
```(notice the \1 and \2) and it seems to be working for me!

Just in case if anyone is looking how to do this on Google sometime in 2014 or so and the find this thread
Something I don't quite get is that you confirmed (2 Weeks Ago 10:25 PM)  that my method worked, and then you are back to yours that doesn't work, and then you fix it by going back to something that looks a lot like my original suggestion :-k

---

### Post by geirha on 2011-10-11
You can match start of word and end of word with \< and \>. (A word in this context consists of [A-Za-z0-9_])

```
$ sed 's/\<usr\>/NEW/g' <<< "%usr% 4usr4 .usr."
%NEW% 4usr4 .NEW.

```

This syntax is portable to other implementations of sed.

---

### Post by nerdopolis on 2011-10-17
> **ofnuts said:**
> Something I don't quite get is that you confirmed (2 Weeks Ago 10:25 PM)  that my method worked, and then you are back to yours that doesn't work, and then you fix it by going back to something that looks a lot like my original suggestion :-k

I realized that the previous method was deleting the two wild card chars as well and replacing it. The old method that I was using wasn't doing that, the first one wasn't acting on all the chars... You then helped me with the (\W|^) and (\W|$), but that was deleting the two chars next to itso I integrated that with my old one... ...That worked until I came across two usr's on a line where one should have been replaced, and one should not have been, but they both got replaced. I then used your method again, but I found a way to get the two chars it was replacing back with \1 and \2 from some site.

---

### Post by ofnuts on 2011-10-18
> **nerdopolis said:**
> I realized that the previous method was deleting the two wild card chars as well and replacing it. The old method that I was using wasn't doing that, the first one wasn't acting on all the chars... You then helped me with the (\W|^) and (\W|$), but that was deleting the two chars next to itso I integrated that with my old one... ...That worked until I came across two usr's on a line where one should have been replaced, and one should not have been, but they both got replaced. I then used your method again, but I found a way to get the two chars it was replacing back with \1 and \2 from some site.
My method used "\1" and "\2", you didn't copy it faithfully enough :)

---

### Post by nerdopolis on 2011-10-18
> **ofnuts said:**
> My method used "\1" and "\2", you didn't copy it faithfully enough :)

Oh... look at that! :p 

I think I was sorta sick that day... ...Thats probably why I didn't see it too well...

---

