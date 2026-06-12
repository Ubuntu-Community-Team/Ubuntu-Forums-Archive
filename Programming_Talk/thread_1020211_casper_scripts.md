---
title: "casper scripts"
date: 2008-12-23
forum: Programming Talk
---

### Post by ralphz on 2008-12-23
Hi

I was playing around with creating my own custom live cd. It come out quite good but i don't understand few aspects of the initramfs and casper scripts.

Script initramfs-tools/scripts/casper-bottom/10adduser has following lines to add user that live system will be running as:

chroot /root debconf-communicate -fnoninteractive casper > /dev/null <<EOF
set passwd/root-password-crypted *
set passwd/user-password-crypted U6aMy0wojraho
set passwd/user-fullname $USERFULLNAME
set passwd/username $USERNAME
set passwd/user-uid 999
EOF

I was trying to find some good articles what kind of options i can use here or what is actually going on here. Can anyone point me to some good resources about that?

Thanks

Ralph

---

