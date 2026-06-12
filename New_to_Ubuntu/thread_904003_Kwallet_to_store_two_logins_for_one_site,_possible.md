---
title: "Kwallet to store two logins for one site, possible ?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by medya on 2008-08-28
hey, I started using Kwallet it is cool, 
it stored my login passwords for diffrent websites , 

but I have two Gmail accounts, one of them was added autoamticly when I entered gmail , but for the second one I didnt get prompt  , and it wasnt added to Kwallet, what should I do ?

---

### Post by vikram on 2008-08-28
How would that be usefull ? If Kwallet stored multiple passwords for the same page which one will be automatically populated ?

If you want to store misc passwords - you can click on the Kwallet icon, open the wallent and add new folders or items with passwords etc.

---

### Post by medya on 2008-08-28
well I want all my passwords to be stored safely and I didnt undrestand what u said about folders... 

let say for gmail I have 3 gmail account and I wanna save all the passwords safely.
how would I do that ?

---

### Post by lovinglinux on 2008-08-28
Have you tried KeePassX? Is a port of Windows KeePass.

It doesn't have embedded integration with the browser but while viewing a page with login form you can open KeePassX and hit "Perform AutoType" and it will fill the form for you. The advantage is that you can easily store passwords for things that do not run inside the browser, like games for example.

KeePass has an option to encrypt the database with a master password, a key file or both. So even if someone discover your master password he will still need the key file to open it.

---

### Post by medya on 2008-08-29
that sounds great , I think Kubuntu should use this instead of Kwallet , it looks more intresting

---

### Post by vikram on 2008-08-29
IMHO Kwallet integrates well with KDE apps like storing your all your Instant Messenger passwords for Kopete, passwords for websites for the konqueror browser, email passwords for Kmail, Network encyrption password for KNetworkManager. That saves a lot of cutting and pasting !!!

If you want to use Kwallet, click on the wallet icon, open a wallet. If this is your first time it will ask for a master password. you can right click anywhere and click on new folder call. After that right click the new folder to add items to store securely.

Hope this helps

---

### Post by medya on 2008-08-29
> **vikram said:**
> IMHO Kwallet integrates well with KDE apps like storing your all your Instant Messenger passwords for Kopete, passwords for websites for the konqueror browser, email passwords for Kmail, Network encyrption password for KNetworkManager. That saves a lot of cutting and pasting !!!

If you want to use Kwallet, click on the wallet icon, open a wallet. If this is your first time it will ask for a master password. you can right click anywhere and click on new folder call. After that right click the new folder to add items to store securely.

Hope this helps

vikram can u tell me what should I do , if I have three Gmail accounts and I access all of them everyday...how am I am gonna store their passwords in kwallet ?

---

### Post by vikram on 2008-08-30
> **medya said:**
> vikram can u tell me what should I do , if I have three Gmail accounts and I access all of them everyday...how am I am gonna store their passwords in kwallet ?
 Please create a folder for example mypasswords by rightclicking anywhere in the open wallet. right click on the new folder. by defaultg 4 folders are created under it. Right Click on "Password" and choose new to add a new passowrd. to this for each of your gmail accounts. you'll have to cut and paste into the browser.

[http://fosswire.com/2007/09/18/kwallet-remembering-passwords-the-kde-way/](http://fosswire.com/2007/09/18/kwallet-remembering-passwords-the-kde-way/)

---

### Post by medya on 2008-08-30
thank u, I will try that, I have got anoterh question , if u dont mind , when I create a new folder , I see things like Binary Data, Maps , Uknown , what are they ?


and anothe question, is there any program in Windows which can uses KWallet data ?

---

### Post by vikram on 2008-09-02
I am not aware of any windows software. You can however use Kwalletmanager for windows though it is currently in a work in progress. I haven't used the other options - I would guess they are used by other KDE apps to store passwords etc.

---

