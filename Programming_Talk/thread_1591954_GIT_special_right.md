---
title: "GIT special right?"
date: 2010-10-10
forum: Programming Talk
---

### Post by huangyingw on 2010-10-10
Hello 
    I am struggling with git now. I wonder git need special right, in order to work correctly?
    See following example.
    ```
huangyingw@Ubuntu10:~/myproject/git/linux/bashrc$ git clone --bare /media/smb/myproject/git/linux/bashrc/ /media/smb/myproject/git/linux/bashrc.bak/
/media/smb/myproject/git/linux/bashrc.bak/refs: Permission denied
huangyingw@Ubuntu10:~/myproject/git/linux/bashrc$ mkdir /media/smb/myproject/git/linux/temp
huangyingw@Ubuntu10:~/myproject/git/linux/bashrc$ mkdir /media/smb/myproject/git/linux/ba
backup/ bashrc/ 
huangyingw@Ubuntu10:~/myproject/git/linux/bashrc$ mkdir /media/smb/myproject/git/linux/ba
backup/ bashrc/ 
huangyingw@Ubuntu10:~/myproject/git/linux/bashrc$ mkdir /media/smb/myproject/git/linux/bashrc/refs/temp
```
      /media/smb is my mounted smbfs filesystem.
      When I run git clone --bare, it prompts me that permission denied.
      While I could mkdir under that directory...:(:(
      But, I could mkdir in that

---

