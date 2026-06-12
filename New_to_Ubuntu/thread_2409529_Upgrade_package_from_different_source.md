---
title: "Upgrade package from different source"
date: 2019-01-03
forum: New to Ubuntu
---

### Post by robertzito on 2019-01-03
I installed VLC and Virtualbox from the software applicatio center, in looking at the vendors sites there are newer version but the ubuntu shop still has the older ones. Is there any way to upgrade these packages form the vendor site.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]robertzito[/COLOR]**]("https://ubuntuforums.org/member.php?u=1845309"),

What version of Ubuntu are you running?

I believe that starting from Ubuntu 16.04 LTS, Ubuntu Software has been updated to return snaps (or snappy) packages in your searches.

On Ubuntu 18.10, a quick search for VLC showed that the top result comes from the Snap Store and is VLC 3.0.5-1 (which I believe is the latest version according to the VLC website).

Regarding VirtualBox, their official [Downloads page]("https://www.virtualbox.org/wiki/Linux_Downloads") is pretty complete and explains how to manually install version 6.0 on Debian and its derivatives (which Ubuntu is based on).

---

### Post by Impavidus on 2019-01-03
For most applications, the version in the Ubuntu repositories is frozen before release. You only get important bug fixes. This is to increase stability. But it is indeed possible to install upgrades from other sources. The thing you're looking for is a [PPA]("https://help.ubuntu.com/community/PPA"). If you really need the features of a more receny version, a PPA will give you that, at the cost of some reliability and security.

Alternatively, you can try and find the newer version of the software in a snap package. Snaps are more secure than PPAs, but come with some disadvantages. I've never used any snaps.

---

