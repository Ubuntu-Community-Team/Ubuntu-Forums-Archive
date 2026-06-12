---
title: "test webserver"
date: 2006-10-04
forum: Programming Talk
---

### Post by rizzy on 2006-10-04
Ok I am not sure how to get this to work, I am sure it is simple, but I just can't seem to figure it out. I installed a test webserver and I have multiple websites. In the apache www folder I want to make folders for each of my sites. Doing this causes all the links to be off.

If I have a folder website1 and I go to 127.0.0.1/website1/ and click on a link it takes me to 127.0.0.1/linkfolder/ when I don't understand why it does not go to 127.0.0.1/website1/linkfolder/

Obviously I could make the links with /website1/ attached at the beginning of each link but this will mess everything up when I want to upload it to my server.

Thanks for any help.

---

### Post by pod25 on 2006-10-04
you need to jump into the said folder:
So if your link is in one subfolder above it needs to be ./linkfolder  and if it is 2 folders up then ../linkfolder

Hope this helps.

---

