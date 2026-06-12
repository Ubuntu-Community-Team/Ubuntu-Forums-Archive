---
title: "Bash sudo and zenity --password"
date: 2012-09-04
forum: Programming Talk
---

### Post by DarkAmbient on 2012-09-04
Writing an installation-script for Minecraft, been trying to get the user to input password, check password and on wrong password as if the user would like to try again or abort. Finally came up with what seems a working solution (for adding a entry to the application-menu), but now I wonder if this unsafe in any way? Is there a better solution?


```
  while ! zenity --password| sudo -S cat /dev/null >/dev/null; do
    if $(zenity --question --text="Wrong password, would you like to cancel the installation?"); then
      echo "no app-entry made, returning"
      return;
    fi
  done
    echo "$appEntry" | sudo -S tee ${launcher}
    sudo -K # remove privilege

```
where appEntry is the text, launcher is the file.

I might add that I would like to use zenity, not gksu or similar.

Thanks

---

### Post by Habitual on 2012-09-04
What logically happens when the user-run install script gets to:
```
sudo -S cat /dev/null >/dev/null; do
```?

---

### Post by DarkAmbient on 2012-09-04
Ok, the way I've understood things.. correct me if I'm wrong, I'm still kinda new to bash.

The -S parameter with sudo tells sudo to read password from the stdin. And cat /dev/null > /dev/null really doesent do anything other than acting as a dummy to use with sudo, or atleast thats my guess. Found it like that one some site :redface:

I guess using ```
while ! zenity --password | sudo -S echo ''; do
```
(or something similar) does just about the same, or is there any difference?

---

### Post by sisco311 on 2012-09-04
Use gksu or pkexec. It is NOT your job (as the writer of the script) to decide how many times the user is allowed to re-type the password.

---

### Post by DarkAmbient on 2012-09-05
> **sisco311 said:**
> Use gksu or pkexec. It is NOT your job (as the writer of the script) to decide how many times the user is allowed to re-type the password.

Point taken, I'll use gksu instead. gksu comes with Ubuntu as default right?

---

### Post by Habitual on 2012-09-05
> **DarkAmbient said:**
> ...correct me if I'm wrong, I'm still kinda new to bash. No, but I'll give you props for reading the man file. :)

> **DarkAmbient said:**
> The -S parameter with sudo tells sudo to read password from the stdin...

You missed it...the script assumes the user has sudo privs...
Did you intend that?

unless Wed Sep 05, 2012 -  6:40:03 AM EDT is too early to be reading forum posts?

I'd have to defer to whatever sisco311 says, he's a master.

Subscribed with interest,

---

### Post by DarkAmbient on 2012-09-05
haha thank you :)

Hm, I'm not following, what I've read about /dev/null is that it's a "special-file" that empties output thrown at it.

Knowing that, I really didn't think that anything special would happen with "cat /dev/null > /dev/null", do you mean we assume the user has sudo-privileges because of that part, or because of the "sudo -S"?

Soo slow after a 9h-workday, sorry... ><

---

### Post by Habitual on 2012-09-05
Well. I am going to back away from the keyboard on this one and let you resume your quest uninterrupted by me.

Have a Great Day!

---

### Post by Paddy Landau on 2012-09-06
I'll weigh in on this, because I've spotted a couple of things.

[LIST]
[*]Rather than use [FONT=Lucida Console]cat[/FONT] [FONT=Lucida Console]>/dev/null[/FONT] as your null process, use something much simpler. The null command, which is just a colon ("[FONT=Lucida Console]:[/FONT]"), is ideal, but it doesn't work for [FONT=Lucida Console]sudo[/FONT] (it doesn't like built-in commands), so then I use [FONT=Lucida Console][[/FONT] [FONT=Lucida Console]1[/FONT] [FONT=Lucida Console]][/FONT].
[/LIST]

[LIST]
[*]I agree with sisco311; use [FONT=Lucida Console]gksudo[/FONT], as it is designed for that purpose. (BTW, I would suggest [FONT=Lucida Console]gksudo[/FONT] rather than [FONT=Lucida Console]gksu[/FONT].) You can, of course, use [FONT=Lucida Console]zenity[/FONT] instead of [FONT=Lucida Console]gksudo[/FONT], but I think it's safer to use [FONT=Lucida Console]gksudo[/FONT] because of its design.
[/LIST]

Here is how I prompt for the user's password. Adapt it to suit your purposes.

```
[COLOR=Navy]# Prompt for the password. [FONT=Tahoma]*Replace "the process" with a meaningful message.*[/FONT][/COLOR]
SUDOPASSWORD="$( gksudo --print-pass --message 'Provide permission for [FONT=Tahoma]*the process*[/FONT]. Type your password, or press Cancel.' -- : 2>/dev/null )"

[COLOR=Navy] # Check for null entry or cancellation.[/COLOR]
if [[ ${?} != 0 || -z ${SUDOPASSWORD} ]]
then
    [COLOR=Navy]# Add a zenity message here if you want.[/COLOR]
    exit 4
fi

[COLOR=Navy] # Check that the password is valid.[/COLOR]
if ! sudo -kSp '' [ 1 ] <<<"${SUDOPASSWORD}" 2>/dev/null
then
    [COLOR=Navy]# Add a zenity message here if you want.[/COLOR]
    exit 4
fi
```Now you can just use the password in your [FONT=Lucida Console]sudo[/FONT] command. You'll notice that I used a Here String instead of a pipe:
```
sudo -Sp '' -- tee "${launcher}" <<<"${SUDOPASSWORD}"
```I have to say that I'm not sure what will happen with [FONT=Lucida Console]tee[/FONT], as the input ([FONT=Lucida Console]stdin[/FONT]) will be the [FONT=Lucida Console]sudo[/FONT] password. What were you trying to do with [FONT=Lucida Console]tee[/FONT]?

---

### Post by Paddy Landau on 2012-09-06
Of course, you could bypass all that complication by just using [FONT=Lucida Console]gksudo[/FONT] for the command itself:
```
gksudo --message 'Provide permission for [FONT=Tahoma]*the process*[/FONT]. Type your password, or press Cancel.' -- tee "${launcher}"
```

---

### Post by DarkAmbient on 2012-09-06
Hi, thanks for joining in and helping out! :)

Well, idk if I've made some terrible misstake with the code-snippet I provided as I got the feeling that I'm getting missunderstood... The goal is to write the text $entry to the file $launcher

> gksudo --message 'Provide permission for the process. Type your password, or press Cancel.' -- tee "${launcher}"

How do tee know what to write to $launcher using that way?

$launcher is in this case "/usr/share/applications/minecraft.desktop", therefore the need for sudo

Managed to do what I want with starting a shell as sudo, and write from inside there. Thank you for telling me how to check password first Paddy Landau! :)

So does this look ok?

```
createMenyEntry() {

  local entry="
[Desktop Entry]
Version=1.0
Type=Application
Name=Minecraft
Comment=Minecraft is a game about placing blocks to build anything you can imagine. At night monsters come out, make sure to build a shelter before that happens. It also has music by C418!
Exec=sh ${starterScript}
Icon=${icon}
Path=${minecraftDir}
Terminal=false
Categories=Game
StartupNotify=true";
 
  local pswrd="$(gksudo --print-pass --message '<b>Provide password to add Minecraft to your application-menu.</b>' -- : 2>/dev/null )" 

   # Check for null entry or cancellation.
  if [[ ${?} != 0 || -z ${pswrd} ]]
  then
      echo "cancel of no password"
      return 1
  fi

   # Check that the password is valid.
  if ! sudo -kSp '' [ 1 ] <<<"${pswrd}" 2>/dev/null
  then
      echo "wrong password"
      return 1
  fi

  echo $pswrd | sudo -S sh -c "echo \"${entry}\" | sudo tee $launcher 2>&1>/dev/null"
  return 0
}
```

---

### Post by Paddy Landau on 2012-09-06
> **DarkAmbient said:**
> So does this look ok?
Well, here are some comments to help you in your learning:

[LIST]
[*]You have called your function [FONT=Lucida Console]createMenyEntry[/FONT]. Did you mean [FONT=Lucida Console]createMenuEntry[/FONT]?
[/LIST]

[LIST]
[*]There is a semi-colon, which you don't need, after the first [FONT=Lucida Console]local[/FONT] statement. (It won't hurt, but it does look a bit odd.)
[/LIST]

[LIST]
[*]Your two [FONT=Lucida Console]local[/FONT]  entries can have the [FONT=Lucida Console]-r[/FONT] option (read-only) to clarify that they should  not be changed after being set. This will tighten your code against  bugs.
[/LIST]

[LIST]
[*]You have used [FONT=Lucida Console]echo[/FONT] to display errors &#8212; if you are running it in the terminal, why bother with [FONT=Lucida Console]gksudo[/FONT]? [FONT=Lucida Console]sudo[/FONT] would do, unless [FONT=Lucida Console]echo[/FONT] is simply there for debugging.
[/LIST]

[LIST]
[*]You use [FONT=Lucida Console]tee[/FONT]. Why not use [FONT=Lucida Console]echo[/FONT]?
[/LIST]

[LIST]
[*]Again, instead of using a pipe, use the Here String. It is cleaner (easier to understand), doesn't start a child process, and the result of the command is available to the script through [FONT=Lucida Console]${?}[/FONT].
[/LIST]

[LIST]
[*]Where you use [FONT=Lucida Console]$launcher[/FONT], do remember to quote the variable in case the file name should have spaces. Even though it doesn't in this particular case, it's a good habit to get into: [FONT=Lucida Console]"${launcher}"[/FONT] (including the quotation marks).[FONT=Lucida Console]
[/FONT]
[/LIST]

[LIST]
[*]Finally, your last statement is pretty complex:```
echo $pswrd | sudo -S sh -c "echo \"${entry}\" | sudo tee $launcher 2>&1>/dev/null"
```Use a Here String instead of the first pipe, use [FONT=Lucida Console]echo[/FONT] instead of [FONT=Lucida Console]tee[/FONT], and use [FONT=Lucida Console]&>/dev/null[/FONT] instead of [FONT=Lucida Console]2>&1>/dev/null[/FONT].
[/LIST]
**But&#8230;**

This is Linux! Why not find a *single* command (if possible) to replace your entire function?

Instead of simplifying your complex code, you can still bypass **all** that complexity with *just a single command*. Check this out:
```
gksudo --message '<b>Provide password to add Minecraft to your application-menu.</b>' -- bash -c "echo '${entry}' >'${launcher}'"
```HTH

---

### Post by DarkAmbient on 2012-09-06
Sweet, thanks for all the pointers and help! 

Well, first of, the createMenyEntry is a typo as meny is swedish for menu. And as you mentioned, the echo's in my script is mainly for debugging, I would like to keep it non-CLI:ish. But I'll update my script some more tomorrow following the rest of your pointers. I tried adding the one-line gksu-example your provided already, works nicely! :)

I'm not to familiar with Here-strings yet tbh.. But now I got something to read about tomorrow! ;) 

I've uploaded what I've done so far in this thread [here]("http://ubuntuforums.org/showthread.php?t=2052084"), but will redo and probably re-upload again tomorrow.

Now, bedtime!

Thanks and good night ):P

---

### Post by Paddy Landau on 2012-09-07
Good, it seems as though you have it solved. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Here Strings: Use [FONT=Lucida Console]man[/FONT] [FONT=Lucida Console]bash[/FONT] and search for *Here Strings* (I don't know what it might be called in Swedish), or see the [on-line manual]("http://www.gnu.org/software/bash/manual/bashref.html#Here-Strings").

To avoid CLI, use [FONT=Lucida Console]zenity[/FONT] instead of [FONT=Lucida Console]echo[/FONT].

Regarding [FONT=Lucida Console]zenity[/FONT]: If you are using it just for yourself, I recommend using [[FONT=Lucida Console]yad[/FONT]]("http://code.google.com/p/yad/") instead ([[FONT=Lucida Console]yad[/FONT]'s repository]("https://launchpad.net/~webupd8team/+archive/y-ppa-manager")). Unfortunately, [FONT=Lucida Console]yad[/FONT] is not in the standard repositories, so you still need [FONT=Lucida Console]zenity[/FONT] when writing for other people.

---

### Post by DarkAmbient on 2012-09-07
Marked as solved!

Yea, I read about yad as an alternative somewhere. But I'm writing this installer mainly for people who has trouble with getting Minecraft to run, so it's a no go im afraid.

Thanks again for all the help Paddy! :)

---

