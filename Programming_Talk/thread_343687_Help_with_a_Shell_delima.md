---
title: "Help with a Shell delima"
date: 2007-01-21
forum: Programming Talk
---

### Post by rekahsoft on 2007-01-21
Hi all, i have written a script that deals with encrypting/decryting GAIM's account configuration file. Currently it checks to see if the config file is encrypted. If so it decrypts it using gpg (the user must enter a password into the console). Then when GAIM is closed it encrypts GAIM's configuration file and removes the plain text config file. The problem is that GAIM has to be run with the console open for this to work. Is there a way to close the console mid way through the script? Or is there some way to have code be run after the process ends? Thanks.

Here is the script (for reference):```
#/bin/sh

arguments=
gpg_key_id="rekahsoft@gmail.com"

# Turns off the encryption
unsecure_game() {
	if [ ! -f ~/.gaim/accounts.xml ]; then
		if [ -f ~/.gaim/accounts.xml.gpg ]; then
			gpg --output ~/.gaim/accounts.xml --decrypt ~/.gaim/accounts.xml.gpg
			rm ~/.gaim/accounts.xml.gpg
		else
			echo "You encrypted account information has been lost!!"
			exit 0
		fi
	fi
}

# decrypts account information file
open_gaim() {
	if [ -f ~/.gaim/accounts.xml.gpg ]; then
		gpg --output ~/.gaim/accounts.xml --decrypt ~/.gaim/accounts.xml.gpg
	fi
	gaim $arguments
}

# encrypts account information file
close_gaim() {
	if [ ! -f ~/.gaim/accounts.xml.gpg ]; then
		gpg --output ~/.gaim/accounts.xml.gpg --encrypt --recipient $gpg_key_id ~/.gaim/accounts.xml
	fi
	rm ~/.gaim/accounts.xml
}

while [ "$1" != "" ]; do
	arguments=$arguments" "$1
	shift
done

open_gaim
close_gaim
exit 0
```

---

### Post by jpeddicord on 2007-01-21
Instead of using just `gaim` to launch it, use `gaim&`. I think that is all you need to do it. :)
The & tells the shell to run it in the background. To bring it to the front, use the `fg` command.

Jacob

---

### Post by rekahsoft on 2007-01-21
> **jacobmp92 said:**
> Instead of using just `gaim` to launch it, use `gaim&`. I think that is all you need to do it. :)
The & tells the shell to run it in the background. To bring it to the front, use the `fg` command.

Jacob

ok...i added '&' to the end of 'gaim' and the script no longer works...I have to be able to let gpg recieve input (the users gpg key)

---

