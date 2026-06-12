---
title: "Accessing ext4 timestamps from extended attributes?"
date: 2015-01-31
forum: Programming Talk
---

### Post by qyot27 on 2015-01-31
As is fairly common knowledge by now, ext4 has a 'crtime' timestamp that provides the Creation (or Birth) Time of a file, and that this information is not exposed to stat because of continuing back-and-forth in the Linux kernel development process.  It is possible to pull the information out of the file's inode with debugfs and parse it, though, and I did that manually for a while.  Then I actually [found a script](https://gist.github.com/ashayh/4570187) that automated the process, but its output was a bit too basic.  [So I modified it to re-insert the information back into the normal readout from stat.](https://gist.github.com/qyot27/5b7b05b86915840536f0)

But since it still requires debugfs to get the information from the inode, it still depends on having root privileges.  Having to use sudo on a stat call is a bit jarring/annoying.

In messing around with an NTFS recovery problem a week or so ago, I discovered that NTFS-3G exposes the timestamp info in the extended attributes.  Because it does this, I could use regular user privileges to get the info, making the experience pretty much seamless.

My question is whether ext4's timestamps are also accessible through the extended attributes so that I wouldn't have to use debugfs anymore.  A more general question is 'how do I know what extended attributes a filesystem exposes?' Is there a system call or something that lists them, or is it a matter of trying to dig through online kernel documentation to maybe, possibly, hope to glean the list of xattrs from a ton of other implementation details?

---

