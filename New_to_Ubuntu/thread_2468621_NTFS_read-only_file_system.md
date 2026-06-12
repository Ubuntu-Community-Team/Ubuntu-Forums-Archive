---
title: "NTFS read-only file system"
date: 2021-11-05
forum: New to Ubuntu
---

### Post by nginmu on 2021-11-05
SOLVED
solution used
```

# add support for MS Win NTFS if not already installed
sudo apt install ntfs-3g -y
# sudo ntfsfix /dev/your_drive to clear 'read only file system'
# due to dirty bit being set
# (or just run Windows chkdsk)

```

I have a 'spare' 1TB HDD in my laptop. Lubuntu and Windows are installed dual-boot on a seperate SSD in the same laptop.

I decided to format the 1TB (conventional / spinning) HDD as NTFS & put my Firefox profile folder on it, so I can run Firefox in both Lubuntu & Windows from the same profile.

This has worked fine for me previously, using an external USB HDD and FAT32.

This time, Firefox won't start, sometimes "Firefox is already running, please close the old process" or somesuch (even though it isn't), sometimes, "Your profile folder is missing or unavailable" (even though it isn't missing)

I did try accessing the profile folder through PCManFM-Qt File Manager but received a message "Read-only file system" when trying to test it by creating a blank file:

```
Error opening file &#8220;/media/me/CrossPlatform/FIREFOX/New text file&#8221;: Read-only file system
```

Permissions of my profile folder (after formatting drive as NTFS & copying profile folder to it using Windows, from a FAT32 drive:

Owner: me (my user name)
Group: me (my user name)
Owner / Group / Other Access: All set to "View and modify folder content"

Not sure what to do next, don't want to start randomly messing about with permission settings, I find if one starts doing that rashly without knowing what one's doing it usually leads to tears.

---

### Post by bunny9000 on 2021-11-06
So the drive was accessible by Windows and not Linux or both.

Glad the fix you found worked.=d>

---

### Post by nginmu on 2021-11-07
Windows was happy with it from the start, Linux was being cautious and not allowing write access until the dirty bit was cleared. I ended up using the Windows 'check drive for errors' GUI tool in disk properties, which afaik effectively runs Windows chkdsk. It was just easier than using ntfsfix because I was already in Windows at the time. Also, others have suggested one should ideally use Windows tools to operate on Windows filesystems.

---

