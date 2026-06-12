---
title: "Executing a script from anywhere."
date: 2013-07-08
forum: New to Ubuntu
---

### Post by TheFallout1994 on 2013-07-08
Greetings !

I have downloaded LinCaml from jean.mouric.pagesperso-orange.fr/[COLOR=#666666][FONT=arial]&#8206; which I use to program in Caml Light. I have successfully followed the instructions that were in the Readme file and installed LinCaml.
Now, I can launch LinCaml from the terminal by going in ~/LinCaml4 and entering ./LinCaml
But I would like to just enter LinCaml in the command line and launch it from anywhere, even if I'm not in the LinCaml4 directory. So I looked it up to know how to do it, and I've been led to copy the ./LinCaml script in [/FONT][/COLOR]./usr/local/bin/LinCaml and used chmod 700 (no need for other users to be able to access it).
I thought it would work, but now when I open a new file, although a window does open, I get an error message that says Caml light toplevel was not found. And there is no way for me to compile and execute any code.

There's nothing urgent, because I can still launch LinCaml from the LinCaml4 directory, or just launch it in the graphic interface.
But just out of curiosity, how could I manage to make it work ? Would it be of any use to copy the whole directory in usr/local/bin ? I've tried to just copy the lintoplevel64 script from ~/LinCaml4/caml-light/bin/ to ./us/local/ ... but it was of no avail.

Thank you for your time.

---

### Post by coldcritter64 on 2013-07-08
To launch an application directly in terminal add the folder that contains the executable to your system path.

To check your system path at any time use the command in terminal,
```
echo $PATH
```

To add the folder to the path edit the file .profile and add the line below with the export command. Save the file and logout of your desktop, then log back in and check the entry in the system path. Codes to do so;
1. 
```
cd ~ && gedit .profile
```
2. In gedit at the end of the file add the line
```
export $PATH=$PATH:$HOME/LinCaml4
```
3. Now log out and back in.
4. Run the echo command shown above to check the system PATH entry for LinCaml4 directory. If it is there you can just enter the executable name in the terminal or create a launcher (desktop configuration file) etc to open it.

Cheers.

---

