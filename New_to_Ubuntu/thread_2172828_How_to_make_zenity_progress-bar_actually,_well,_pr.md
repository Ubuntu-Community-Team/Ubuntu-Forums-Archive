---
title: "How to make zenity progress-bar actually, well, progress"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-06
Hello all!

I have a couple of commands that I want to run, and I want a zenity progress-bar to integrate to the commands:). Unfortunately, I only know how to get the progress-bar to appear, not how to actually make it move:(. Is there any special way to do this?[INDENT]Update: Here are the screenshots.[/INDENT]

---

### Post by rai_shu2 on 2013-09-06
You advance the bar by piping the value to the command. See [https://help.gnome.org/users/zenity/stable/progress.html.en](https://help.gnome.org/users/zenity/stable/progress.html.en)

---

### Post by Crusty Old Fart on 2013-09-06
Here's a working example that keeps the Zenity message box on top using wmctrl.
if you don't have wmctrl installed, you can comment out the **[COLOR=blue]blue line[/COLOR]** in the code box below:
```

#!/bin/bash

# Force Zenity Status message box to always be on top.
**[COLOR=blue]sleep 1 && wmctrl -r "Progress Status" -b add,above &[/COLOR]**

(
# =================================================================
echo "# Running First Task." ; sleep 2
# Command for first task goes on this line.

# =================================================================
echo "25"
echo "# Running Second Task." ; sleep 2
# Command for second task goes on this line.

# =================================================================
echo "50"
echo "# Running Third Task." ; sleep 2
# Command for third task goes on this line.

# =================================================================
echo "75"
echo "# Running Fourth Task." ; sleep 2
# Command for fourth task goes on this line.


# =================================================================
echo "99"
echo "# Running Fifth Task." ; sleep 2
# Command for fifth task goes on this line.

# =================================================================
echo "# All finished." ; sleep 2
echo "100"


) |
zenity --progress \
  --title="Progress Status" \
  --text="First Task." \
  --percentage=0 \
  --auto-close \
  --auto-kill

(( $? != 0 )) && zenity --error --text="Error in zenity command."

exit 0

```

---

### Post by Jonathan Precise on 2013-09-07
> **Crusty Old Fart said:**
> Here's a working example that keeps the Zenity message box on top using wmctrl.
if you don' have wmctrl installed, you can comment out the **[COLOR=blue]blue line[/COLOR]** in the code box below:
```

#!/bin/bash

# Force Zenity Status message box to always be on top.
**[COLOR=blue]sleep 1 && wmctrl -r "Progress Status" -b add,above &[/COLOR]**

(
# =================================================================
echo "# Running First Task." ; sleep 2
# Command for first task goes on this line.

# =================================================================
echo "25"
echo "# Running Second Task." ; sleep 2
# Command for second task goes on this line.

# =================================================================
echo "50"
echo "# Running Third Task." ; sleep 2
# Command for third task goes on this line.

# =================================================================
echo "75"
echo "# Running Fourth Task." ; sleep 2
# Command for fourth task goes on this line.


# =================================================================
echo "99"
echo "# Running Fifth Task." ; sleep 2
# Command for fifth task goes on this line.

# =================================================================
echo "# All finished." ; sleep 2
echo "100"


) |
zenity --progress \
  --title="Progress Status" \
  --text="First Task." \
  --percentage=0 \
  --auto-close \
  --auto-kill

(( $? != 0 )) && zenity --error --text="Error in zenity command."

exit 0

```

Thank you for the script!! I adapted it to run maintenance tasks. Here it is:

```
#!/bin/bash

(
# =================================================================
# Configure un-configured packages
echo "# Doing package maintenance" ; sleep 2
gksu "gnome-terminal -x dpkg --configure -a"


# =================================================================
# Run Software Updater...
echo "25"
echo "# Updating..." ; sleep 2
update-manager


# =================================================================
# Remove extra programs...
echo "50"
echo "# Removing unneeded programs..." ; sleep 2
gksu "gnome-terminal -x apt-get autoremove"


# =================================================================
echo "75"
echo "# Finishing..." ; sleep 2
# Nothing happens here!
sleep 2


# =================================================================
echo "99"
echo "# Finishing..." ; sleep 4


# =================================================================
echo "# All finished." ; sleep 2
echo "100"




) |
zenity --progress \
  --title="Simple Maintenance" \
  --text="First Task." \
  --percentage=2 \
  # --pulsate


if [ "$?" = -1 ] ; then
        zenity --error \
          --text="Update error."
fi
exit 0
```

For a pulsating one:

```
#!/bin/bash

(
# =================================================================
echo "# Doing package maintenance" ; sleep 2
gksu "gnome-terminal -x dpkg --configure -a"


# =================================================================
echo "25"
echo "# Updating..." ; sleep 2
update-manager


# =================================================================
echo "50"
echo "# Removing uneeded programs..." ; sleep 2
gksu "gnome-terminal -x apt-get autoremove"


# =================================================================
echo "75"
echo "# Finishing..." ; sleep 2
# Ignore this line
sleep 2


# =================================================================
echo "99"
echo "# Finishing..." ; sleep 4


# =================================================================
echo "# All finished." ; sleep 2
echo "100"




) |
zenity --progress \
  --title="Simple Maintenance" \
  --text="First Task." \
  --percentage=2 \
  --pulsate


if [ "$?" = -1 ] ; then
        zenity --error \
          --text="Update error."
fi
exit 0
```

Thanks again!

[SIZE=1]*Marked as solved.*[/SIZE]:)

---

### Post by Crusty Old Fart on 2013-09-07
> **Jonathan Precise said:**
> Thank you for the script!!...
You're mighty welcome, Jonathan.

I wrote that script several years ago and have been using it ever since, with success. Consequently, the Zenity error message hasn't appeared. However, after I posted it it here, and saw what the last few lines of the script were, they didn't look right to me. After doing some testing, I found that they really didn't work well. So, I edited my post. Unfortunately, my edit was too late for you to pick up the change. So, I thought I should point out the correction.

**[color=red]This code doesn't really work right:[/color]**
```

if [ "$?" = -1 ] ; then
        zenity --error \
          --text="Update error."
fi
exit 0

```

**[color=green]It should be replaced with the following:[/color]**
```


(( $? != 0 )) && zenity --error --text="Error in zenity command."

exit 0

```
Sorry about that.

```


    Thank you for marking your thread as: [SOLVED].

                         _---_
                        /_/|\_\
                       (/-O^O-\)
                __    /_\\/*\//_\    __
         ------vVVv----- o###o -----vVVv------
                          """

                   Darthroy was here.


```

---

### Post by rai_shu2 on 2013-09-07
That "erroneous" code is straight out of the [Gnome example]("https://help.gnome.org/users/zenity/stable/progress.html.en"), if you notice.

---

### Post by Crusty Old Fart on 2013-09-07
> **rai_shu2 said:**
> That "erroneous" code is straight out of the [Gnome example]("https://help.gnome.org/users/zenity/stable/progress.html.en"), if you notice.
Well, I'll be damned. So, that's where I got it.
It still sucks, though.

---

### Post by Jonathan Precise on 2013-09-13
> **Crusty Old Fart said:**
> You're mighty welcome, Jonathan.

I wrote that script several years ago and have been using it ever since, with success. Consequently, the Zenity error message hasn't appeared. However, after I posted it it here, and saw what the last few lines of the script were, they didn't look right to me. After doing some testing, I found that they really didn't work well. So, I edited my post. Unfortunately, my edit was too late for you to pick up the change. So, I thought I should point out the correction.

**[COLOR=red]This code doesn't really work right:[/COLOR]**
```

if [ "$?" = -1 ] ; then
        zenity --error \
          --text="Update error."
fi
exit 0

```

**[COLOR=green]It should be replaced with the following:[/COLOR]**
```


(( $? != 0 )) && zenity --error --text="Update error."

exit 0

```
Sorry about that.

```


    Thank you for marking your thread as: [SOLVED].


```

Ok. Thank you! I will change that.

---

