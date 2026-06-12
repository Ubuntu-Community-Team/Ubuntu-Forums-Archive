---
title: "execute symlink from pwd"
date: 2010-09-07
forum: Programming Talk
---

### Post by yman on 2010-09-07
I wrote this script in order to be able to install Little Space Duo system-wide:
```
#!/usr/bin/env sh

system="/opt/LittleSpaceDuo/"
user="$HOME/.config/LittleSpaceDuo"
# create the user's configuration folder:
mkdir -p "$user"

# create links for all files needed to run the game in the user's configuration folder:
cd "$system"
for file in *.pak
do
	if test -f "$system/$file"
	then
		ln -s "$system/$file" "$user/$file"
	fi
done
cp "$system/LittleSpaceDuo" "$user/LittleSpaceDuo"

# run the game from the user's configuration folder:
cd "$user"
"./LittleSpaceDuo"

# remove all the links once the game is exited:
for file in *
do
	if test -f "$user/$file"
	then
		echo "$user/$file"
		rm "$user/$file"
	fi
done

```

However, when it executes "$HOME/.config/LittleSpaceDuo/LittleSpaceDuo" the program tries to read and write to "/opt/LittleSpaceDuo" instead of the directory the symlink is in. How can I get it to read and write to the directory in which I placed the symlink?

---

