---
title: "Feedback on first bash script"
date: 2010-08-10
forum: Programming Talk
---

### Post by japhyr on 2010-08-10
Hello,

I just wrote my first bash script, and I'd love some feedback.  The script keeps a list of packages I have installed, so next time I upgrade I run the script once and have all the packages I am used to.  Instead of installing new packages through synaptic, I will add packages to this script and rerun it.  Upgrading should be much easier from now on!

The script works and there's no need to overly polish it, but there are a couple areas where I'm wondering if there is a better approach.

[LIST=1]
[*]Is there a better way to concatenate the list of packages?  I broke it up to fit in an editor better, and also so I can easily comment out lines and install packages in batches.  This should keep me from tying up my network for too long at a time.
[*]Is there a way to set the -e flag for echo for the whole script?
[*]Does "apt-get update" do the same thing as the reload button in synaptic?
[*]Is the structure of the if statement clean and appropriate?
[*]The logging works, but I don't think the -q flag is doing what I expected.  In the log, I see progress messages like "reading database 5%" etc.  I don't see those progress messages on the screen.  I thought screen and log output would be the same with the tee command.  Is there a way to get the progress messages to the screen as well?  Even better, is there a way to send the progress messages to the screen and not to the log?
[/LIST]
```
#!/bin/bash

# Packages to install
#  r, r commander, kdenlive
packages="compizconfig-settings-manager emacs dia-gnome freemind nmap gimp"
packages="$packages openoffice.org-base inkscape digikam scribus"

# Other variables
logFile='/home/eric/scripts/log_install_script_10.04.txt'
numPackagesInstalled=0

# Describe program to user.
echo -e "\nThis script facilitates migration to new versions of ubuntu, and to recreating this environment on new machines. The script installs a variety of programs if they do not already exist on the system. Run the script on a new machine, and current versions of all packages should be installed. A log is kept at $logFile. This script must be run with root privileges.\n\nThe following packages will be installed:\n $packages"

# Update package database first.
echo -e "\nUpdating the package database..."
apt-get update

# Only install packages that have not yet been installed.
for package in $packages;
   do
      if [[ ! (`dpkg -l | grep $package`) ]]
         then

		# Send most output to log and to screen.
		echo -e "\n\n---------- $package ----------\n" >> $logFile
                echo `date -R` >> $logFile				
		echo -e "\nInstalling package $package.\n" | tee -a $logFile

		#  -y answers prompts with default yes, -q means quiet output.
		#  tee sends output to terminal and logFile, -a appends to logFile.
		apt-get -y -q install $package 2>&1 | tee -a $logFile

		let numPackagesInstalled++

      fi;
   done

if [ $numPackagesInstalled -eq 0 ]
	then
		echo -e "\nNo new packages were installed."
fi
```

---

### Post by geirha on 2010-08-10
That's not bad for a first script.

1. I recommend making packages an array instead of a string
```
packages=( 
    compizconfig-settings-manager emacs dia-gnome freemind nmap gimp
    openoffice.org-base inkscape digikam scribus
)
# ... and then to use it in the for-loop
for package in "${packages[@]}"; do
    ...

```
See [http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005) for more.

2. Yes, you could use a function, like echo() { command echo -e "$@"; }, but I recommend against it. I'd rather recommend a here document or printf
```
# heredoc
cat << EOF
This script facilitates migration to new versions of ubuntu, and to recreating this environment on new machines. The script installs a variety of programs if they do not already exist on the system. Run the script on a new machine, and current versions of all packages should be installed. A log is kept at . This script must be run with root privileges.

The following packages will be installed:
 
EOF

```
Run ''help printf'' in an interactive bash shell to see how printf works.

3. Yes.

4. The if is a bit silly. You are checking whether grep is outputting anything, instead of just checking its exit status. Just use grep -q, it returns true if there is a match, false otherwise.
```

if ! dpkg -l | grep -q "$package"; then
    printf "\n\n---------- %s ----------\n" "$package" >> "$logFile"
    ...
fi

```
Though, it's probably better to just use dpkg -s
```
if ! dpkg -s "$package" >/dev/null 2>&1; then
    ...

```

For the second if, do not use [ in a bash script. Use [[ to test strings and files, (( to test integers; so
```
if (( numPackagesInstalled == 0 )); then
    ...

```
You can also use the (( )) syntax instead of let; e.g.
```
(( numPackagesInstalled++ ))
```

5. It does get written to the screen, but that line is repeatedly rewritten until its done. e.g. try this:
```

for i in {0..100..10}; do printf "\rProgress ... %3i%%" "$i"; sleep 0.1; done; printf "\rProgress ... Done\n"

```


On a final note; it's good practice to always quote expansions. "$logFile", not $logFile

---

### Post by japhyr on 2010-08-10
Thank you for the detailed response.  On a first read, most of what you said makes enough sense to digest.  I have a few more scripts to write, and your feedback gives me confidence in moving forward in a more reliable manner.

> On a final note; it's good practice to always quote expansions. "$logFile", not $logFile 
Do you mean I should use
```
echo `date -R` >> "$logFile"
```
instead of
```
echo `date -R` >> $logFile
```
If my understanding is correct, what is the rationale for that?

---

### Post by geirha on 2010-08-10
Well, `` is an expansion too, so ```
echo "`date -R`" >> "$logFile"
```
Though, that in turn is a useless use of echo, because ```
date -R >> "$logFile"
``` will give you the same.

When you leave an expansion unquoted, bash rips the value apart, removing any whitespace it contains, and puts it back together again. Then, if it contains any globs, it tries to replace those with matching filenames (pathname expansion). If you quote the expansion, it simply expands the value, leaving it as one word, and it won't try to match any globs.

If the variable doesn't contain any whitespace or globs, it's ok, but it's still good practice to quote it as it simply won't attempt word splitting and pathname expansion on it if you do quote it.

See pitfall 2 at [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

And lastly, for command substitution, $() is preferred over ``. See [http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

---

### Post by japhyr on 2010-08-11
I have a couple questions as I start to implement some of the suggestions.
```
if ! dpkg -s "$package" >/dev/null 2>&1; then

```
is a much cleaner if statement.  For readability, I like to put some kind of wrapper around the test, such as 
```
if ( ! dpkg -s "$package" >/dev/null 2>&1 ); then...
```
Is it okay to do this, or is there a proper way to do this?  In my experience with other languages, I've never thought of symbols like (, ((, [, and [[ as commands, which they seem to be in bash.

Also, what happens if this script gets interrupted while it is installing a program?  Does it depend when the interruption happens, such as during a download or during an installation?

---

### Post by geirha on 2010-08-12
It'll work the same, but you're starting an unecessary subshell. See [http://mywiki.wooledge.org/SubShell](http://mywiki.wooledge.org/SubShell)

I recommend you don't add those parenthesis, and just accept that bash is not like C or perl or java or ...

An interrupt signal will go to whatever command is currently being run by the script.

---

