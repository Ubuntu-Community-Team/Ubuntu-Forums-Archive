---
title: "Password on Shell script"
date: 2007-10-08
forum: Programming Talk
---

### Post by Mbengi Bongi on 2007-10-08
Hi Guys

How can i set up a prompt for a 'user name' and 'password' on a shell script

ideally what I'd like is:

1. After you type the command into BASH a prompt apprears asking for user name and password

2. After a correct user name and password are entered a message appears like Logging on ..... (with a 5 second delay) then the shell script opens.

If an incorrect username/password is entered an error message appears.

NOTE The user name/password are for this shell script only NOT system wide.

Any help would be welcome

---

### Post by slavik on 2007-10-08
following code has not been tested:
```

echo -n "username: "
if [[ $(readline) ne "user" ]] then
  exit 1;
fi
echo -n "password: "
if [[ $(readline) ne "pass" ]] then
  exit 2;
fi

```

---

### Post by Mbengi Bongi on 2007-10-08
I tried that but i get the following error message:

[COLOR="Indigo"]username: ./sm5.sh: line 5: conditional binary operator expected
./sm5.sh: line 5: syntax error near `ne'
./sm5.sh: line 5: `if [[ $(readline) ne "user" ]] then'[/COLOR]

---

### Post by slavik on 2007-10-08
read up on bash string comparisons, might be that you need to use == ... please excuse my Perl :)

---

### Post by Jacks0n on 2007-10-09
I had to do this a while ago.... I just used a case statement.

```

echo -n "Username: "
read USER
echo -n "Password: "
read PASSWD

case $USER in
        "USER1") PASSWORD="PASSWORD1" ;;
        "USER2") PASSWORD="PASSWORD2" ;;
        "USER2") PASSWORD="PASSWORD3" ;;
esac

if [[ $PASSWORD == $PASSWD ]]; then
        echo "Logging in..."
        sleep 5
        bash /home/$USER/location/of/shell/script.sh
else
        echo "Sorry, wrong login details..."
        exit 1
fi

```

---

### Post by Mbengi Bongi on 2007-10-10
That works a treat Jacks0n, thanks very much. :guitar:

Just one thing

**When logging in....**  appears is there any way I can make the dots extend during the 5 second sleep period?

Thanks in advance :)

---

### Post by bigboy_pdb on 2007-10-12
If you don't want the characters for the password displayed then you can use:
read -s PASSWD

---

### Post by bigboy_pdb on 2007-10-12
To make a new dot appear after each second you can use the following code:
```

echo -n "Logging In"
i=1
while ((i < 5)); do
	echo -n "."
	sleep 1
	((i++))
done
echo

```

---

