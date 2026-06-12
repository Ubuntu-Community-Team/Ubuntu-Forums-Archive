---
title: "bash script help"
date: 2010-01-10
forum: Programming Talk
---

### Post by razzer on 2010-01-10
Hello, i need to help with a bash script. in the code bellow. my problem is that what is read into "text7" wont appear further down in the code when it's adding virtuals into the virtual file "echo $firstname.$surname@$text7.local $firstname >>  /etc/postfix/virtual" why is this ?? also, how can i make it so that when what the script is going to add someting into the virtual file already exists during the loop it adds someting, so it if where to add "johan.svensson@domain.local" to the virtual file and it exists it adds "1johan.svensson@domain.local" insteed?

```
echo argument 1 = $1


echo -n "Enter a filename  > " >/dev/tty
   read text6 </dev/tty


echo -n "What domain is this for ?  > " >/dev/tty
   read text7 </dev/tty


cat $text6 | sed -e "s/[åä]/a/g" -e "s/[ö]/o/" | while IFS=';'  read firstname surname;
do




    echo adding $firstname $surname
    useradd $firstname -m -p Syp9393


    echo Creating Maildir in /home/$firstname/
    cd /home/$firstname/
    maildirmake.courier Maildir


    echo Maildir in /home/$firstname/ Created


    echo Giving Maildir owner and group rights to $firstname
    chown -R $firstname /home/$firstname/Maildir/
    chgrp $firstname /home/$firstname/Maildir/


    echo adding to aliases
    echo $firstname.$surname@$text7.local $firstname >>  /etc/postfix/virtual


    echo Done, Going for next user


done
```

---

### Post by razzer on 2010-01-12
anyone that can help? :/

---

