---
title: "*Really* Easy Shared Folders"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by vyruss on 2006-06-14
Here's a tip for all the people who have been frustrated by this:

In order to fully share a folder (read/write), **right-click** on it and select **Share folder**. Select **Share with: SMB**, type in a **Name:** and you're (almost) done.

*Here's the tricky part everybody stumbles upon:* this is not enough to make your shared folder writable!

You have to **right-click** on the folder again and select **Properties**, go to the **Permissions** tab and check **Read**/**Write** for **Group** and **Others**.

I'm all for security on your network, but when you want to share something immediately, quick'n'dirty, without having to change your samba configuration, this is the trick ;)

Enjoy!

---

