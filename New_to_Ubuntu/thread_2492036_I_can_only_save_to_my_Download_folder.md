---
title: "I can only save to my Download folder"
date: 2023-10-28
forum: New to Ubuntu
---

### Post by paulshaffer4 on 2023-10-28
I recently installed Ubuntu 22 lts, and for some reason I can only save images, like jpg images, to my download folder.  The orange save button is "faded" or shadowed out.  I'm using Firefox.

?

See 2nd image attached - the first image bellow was a mistaken upload.

---

### Post by yancek on 2023-10-28
From the image you posted, it appears you are trying to save a file to the user Desktop directory.  So what happens when you click on Save in the upper right?  Do you see any messages?  Have you tried starting firefox from a terminal to see if you get any messages when you close it?

On my system (20.04) there is a Desktop directory listed in the left panel below Home and above Documents which you don't seem to have?  What happens when you try to save to one of the other directories?  Firefox has Edit/Settings and under Files and Applications, it shows Save files to Downloads as the default and that can be changed.  Below that is a check box 'Always ask where to save file'.  You might try checking that box.

---

### Post by paulshaffer4 on 2023-10-28
> **yancek said:**
> From the image you posted, it appears you are trying to save a file to the user Desktop directory.  So what happens when you click on Save in the upper right?  Do you see any messages?  Have you tried starting firefox from a terminal to see if you get any messages when you close it?

On my system (20.04) there is a Desktop directory listed in the left panel below Home and above Documents which you don't seem to have?  What happens when you try to save to one of the other directories?  Firefox has Edit/Settings and under Files and Applications, it shows Save files to Downloads as the default and that can be changed.  Below that is a check box 'Always ask where to save file'.  You might try checking that box.

I did a sudo update and upgrade and the problem went away.  To answer your question, previously the light orange save button, when it was clicked nothing would happen.

But all is working now after the updtate/upgrade.

Marking as solved.

---

### Post by Impavidus on 2023-10-28
Not sure of this, but using a snap version of Firefox (which is the default nowadays) may come with some more restrictions on the directories you can use. After using a snap Firefox for about 6 months I was so fed up with it that I removed it and switched back to a deb version, so I can't really test it now.

Edit: So this was already solved. We call that an edit conflict.

---

