---
title: "[Lubuntu] Help editing &quot;Language Selection&quot; for Custom Guest Session"
date: 2016-12-21
forum: New to Ubuntu
---

### Post by j.horn on 2016-12-21
Hello,

I am adding the option in a customized guest account for the user to choose their language. I successfully followed the guide here:

[https://help.ubuntu.com/community/CustomizeGuestSession#Language_selection_dialog](https://help.ubuntu.com/community/CustomizeGuestSession#Language_selection_dialog)

And can now choose between English and Swedish (surprise surprise!).

I have no coding experience. This is all a learning exercise for me. So, what/how do I modify it for other languages (the script seems to be set up in an either/or fashion)? Where/how can I find the acronyms needed? ie.:
```
if [ "$guestlang" = 'XXXX' ]; then
        echo 'export LANGUAGE=xxxx_XXXX' >> "$HOME/.profile"
        echo 'export LANG=xxxx_XXXX.UTF-8' >> "$HOME/.profile"
```

 
So far I will need to add the following languages to the list: English, French, Arabic, Korean, Chinese, Hindi, Panjabi, Bangla.

Thank you!

---

### Post by Hadaka on 2016-12-22
Hi, I did a little research and modified your script, it should work.
I am not a zenity user but it seems simple enough,If you need help
finding and adding future country codes,let us know.
Have fun !
________________________________________________________________________
#!/bin/sh -e

# show zenity dialog only when launched from greeter
ONLYGUEST=true
for U in $(users); do
    if [ "${U%%-*}" != 'guest' ]; then
        ONLYGUEST=false
        break
    fi
done

if $ONLYGUEST && [ -x /usr/bin/zenity ]; then
    guestlang=$( zenity --list --title 'Select language' \
      --text 'Select language for the guest session' --radiolist \
      --column 'Pick' --column 'Language' \
      TRUE 'English' \
      FALSE 'French' \
      False 'Arabic' \
      False 'Korean' \
      False 'Chinese' \
      False 'Hindi' \
      False 'Panjabi' \
      Flase 'Bangla' )
    if [ "$guestlang" = 'English' ]; then
        echo 'export LANGUAGE=en_US' >> "$HOME/.profile"
        echo 'export LANG=en_US.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'French' ]; then
        echo 'export LANGUAGE=fr' >> "$HOME/.profile"
        echo 'export LANG=fr_FR.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'Arabic' ]; then
        echo 'export LANGUAGE=ar' >> "$HOME/.profile"
        echo 'export LANG=ar_AE.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'Korean' ]; then
        echo 'export LANGUAGE=ko' >> "$HOME/.profile"
        echo 'export LANG=ko_KR.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'Chinese' ]; then
        echo 'export LANGUAGE=zh' >> "$HOME/.profile"
        echo 'export LANG=zh_CN.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'Hindi' ]; then
        echo 'export LANGUAGE=hi' >> "$HOME/.profile"
        echo 'export LANG=hi_IN.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'Panjabi' ]; then
        echo 'export LANGUAGE=pa' >> "$HOME/.profile"
        echo 'export LANG=pa_IN.UTF-8' >> "$HOME/.profile"
    elif [ "$guestlang" = 'Bangla' ]; then
        echo 'export LANGUAGE=bn' >> "$HOME/.profile"
        echo 'export LANG=bn_BD.UTF-8' >> "$HOME/.profile" 
    fi
fi

exec /usr/lib/lightdm/lightdm-guest-session "$@"

---

### Post by j.horn on 2016-12-23
Wow! Thank you very much! That works perfect. I didn't expect an answer so quickly, let alone one that solves my question completely!

---

