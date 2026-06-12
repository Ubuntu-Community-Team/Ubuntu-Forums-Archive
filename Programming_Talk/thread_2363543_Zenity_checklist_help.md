---
title: "Zenity checklist help"
date: 2017-06-11
forum: Programming Talk
---

### Post by alutins45 on 2017-06-11
```
#!/bin/bash

response=$(zenity --height=350 --width=500 --list --checklist \
    --title="Post install" --column=Nr --column=List \
    FALSE "1. Perform system update & upgrade?" FALSE "2. Install favourite applications?" FALSE "3. Install favourite system tools?" FALSE "4. Install development tools?" FALSE "5. Install Ubuntu Restricted Extras?" FALSE "6. Install third-party applications?" FALSE "7. Configure system?" FALSE "8. Cleanup the system?" FALSE "9. Quit?" --separator=":")


IFS=":" ; for word in $response ; do
    case $word in
    "1. Perform system update & upgrade?") zenity --info --text  "Performing system update and upgrade!" ;;
    "2. Install favourite applications?") zenity --info --text  "Installing favourite applications!" ;;
    "3. Install favourite system tools?") zenity --info --text "Installing favourite system tools" ;;
    "4. Install development tools?") zenity --info --text "Installing development tools!" ;;
    "5. Install Ubuntu Restricted Extras?") zenity --info --text "Installing Ubuntu restricted extras!" ;;
    "6. Install third-party applications?") zenity --info --text "Installing third-party applications!" ;;
    "7. Configure system?") zenity --info --text "Configuring system!" ;;
    "8. Cleanup the system?") zenity --info --text "Cleaning the system!" ;;
    "9. Quit?") zenity --info --text "Quitting!" ;;
esac
done



```

Hello guys, i need help with this script. When i choose one of the options it's working fine. But when i choose multiple options it's create multiple info boxes with one option. I need that if i choose multiple options the outputs are in one info box. sorry for my bad english, it's not my national language and i am newbie at this.

---

### Post by norobro on 2017-06-11
[FONT=arial]I see no reason for you to apologize for your English.

You could build up a string in your for loop and execute zenity once outside the loop.

I tested it with three entries and it seems to work:```
...
string=""
IFS=":" ; for word in $response ; do
    case $word in
    "1. Perform system update & upgrade?") string=$string"Perform system update & upgrade\n" ;; 
    "2. Install favourite applications?") string=$string"Install favourite applications?\n" ;; 
    "3. Install favourite system tools?") string=$string"Installing favourite system tools\n" ;;
...
    esac
done
zenity --info --no-markup --text="$(printf "$string")"
```
The --no-markup is necessary because of the ampersand in choice 1.
The printf expands the string before it gets passed to zenity so the new line is handled properly.[/FONT]

---

