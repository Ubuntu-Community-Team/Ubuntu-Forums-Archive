---
title: "ssh-agent + ssh-add"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by iason on 2008-10-05
every time i run ssh-agent to do a passwordless ssh/scp i need to do ssh-add id_rsa.  I thought after the first time it should store it and would not need to enter the passphrase again?  I seem to have to do this every time? what am i missing?

---

### Post by bodhi.zazen on 2008-10-05
I assume you are asking about the X application, ie the pop-up box that asks for confirmation every time ?

This is "gnome-keyring-manager" and is it supposed to make your life easier. 

I suggest you turn it off.

Open a terminal, enter:

```
gconf-editor
```

Navigate to apps -> gnome-keyring-manager

click the "daemon-components"

unselect ssh and pkcs11

save and exit gconf-editor.

Log off and back on and ssh-agent should now work just fine.

---

### Post by iason on 2008-10-06
actually I just run it from the command prompt.  I dont have a gui at all.

---

### Post by bodhi.zazen on 2008-10-06
try keychain

```
sudo apt-get install keychain
```Then add the key with :

```
keychain ~/.ssh/id_rsa
```

Once your key is loaded, you ssh directly to the server.

ie : ssh user@server

you do not specify and identity id **NOT** ssh user@server -i ~/.ssh/id_rsa

---

