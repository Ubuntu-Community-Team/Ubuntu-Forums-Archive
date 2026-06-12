---
title: "Beginner--Running Scripts From Desktop Launcher"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Joeyjoejoejrshabadoo on 2012-01-19
I've been searching for an hour.  I've made a bash script to launch my ruby on rails environment.  It work well if I open it from a terminal window, but doesn't work if I launch it from the desktop.  It opens all the windows, my editor and a browser window to the current project, but all of the rails commands fail as not being found.

I can't really figure out the differnce between opening a terminal window myself and having a desktop launcher do it.

Any ideas?

Here's my (ugly) code:

```
#!/bin/bash
clear

direc="$HOME/railsprojects"


if [ -d $direc ]; then
	cd $direc
elif [ -e $direc ]; then
	echo "The expected rails project directory is not a directory"
	exit
else 
	echo "The expected rails project directory does not exist"
	exit
fi

echo "Please choose a rails project:"
echo ""
N=0
for i in $(ls -1d */); do
	dirarray=$i
	echo "$N: $i"
	N=$N+1
done

read ans

cd ${dirarray[$ans]}
	


#open sporks guard and server
gnome-terminal --tab --command  "bash -c 'bundle exec spork cucumber;bash -i'" --tab --command  "bash -c 'bundle exec spork rspec;bash -i'" --tab --command  "bash -c 'bundle exec guard;bash -i'" --tab --command  "bash -c 'rails s;bash -i'"

#open tails on the dev log and test log
gnome-terminal --tab --command  "bash -c 'tail -f log/development.log'" --tab --command  "bash -c 'tail -f log/test.log'"

#open firefox

gnome-terminal --tab --command "bash -c 'firefox localhost:3000'"

#open gedit
gmate
```

---

