---
title: "Ubuntu 22.04, problem with uploading (photos) in Firefox, and Chrome"
date: 2022-04-22
forum: New to Ubuntu
---

### Post by pajakod on 2022-04-22
Hello,
when I want to upload an image in efox (ebay, fb), then after moving to upload, the cursor changes classically, I click on the upload icon, but nothing happens. Normally, the filemanager through which the image is uploaded should climb, but this will not happen. When I click on upload, nothing just happens.
I have a similar problem with chrome, there is a way to click and select an image, the image is even uploaded, but chrome completely freezes and can only be shot down via the activity monitor. Tested on ebay, fb, chrome freezes everywhere after uploading photos.
While under Windows 10, absolutely cool.
Ubuntu 22.04, firefox and chrome are updated.
Thanks

---

### Post by #&amp;thj^% on 2022-04-22
This might help,  If you have set your Firefox browser to block pop-up windows, it prevents this window from opening. To resolve this issue, go to the Content tab of the Firefox Preferences window, and then either enable pop-up windows or add eBay to the list of exceptions.
Also related: [https://support.mozilla.org/bm/questions/1365562](https://support.mozilla.org/bm/questions/1365562)

---

### Post by pajakod on 2022-04-24
it did not help

---

### Post by ActionParsnip on 2022-04-25
If you make a fresh Ubuntu user, then log in as that is it OK. Keep the browser as vanilla as possible. Don't log in to Chrome etc

---

### Post by pajakod on 2022-04-25
Problem solved. Firefox must be from the deb repository, not the snap. The snap version is broken!

---

