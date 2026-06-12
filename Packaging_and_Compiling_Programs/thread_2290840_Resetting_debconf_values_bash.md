---
title: "Resetting debconf values bash"
date: 2015-08-15
forum: Packaging and Compiling Programs
---

### Post by McJuicy on 2015-08-15
So I've had a bit of success creating a .deb file and the installation going correctly the first time. I'd like users to be able to reinstall / reconfigure the package with different values, but it seems that debconf is keeping the values stored in the database.

What command do I use in bash to reset these values so I can reprompt the user ? I've tried db_reset and db_purge to no avail. Thanks for the help in advance :)

---

### Post by mc4man on 2015-08-15
sudo dpkg-reconfigure package
ck. man dpkg-reconfigure for more info

---

### Post by McJuicy on 2015-08-15
Maybe this will help clarify. Here is an excerpt of the script I'm using

```
# I'd like to reset the value in the db here if possible before I get the value
db_get interface/outface
OUT_FACE=$RET
```

So what happens is that when someone re-runs the install script, it will default to the value they provided as a string the previous time. How can I clear this value?

Also, is there a way to dynamically build questions based on the system in debconf? I wan't to prompt the user about the interfaces they are using instead of asking them to input the string of the interface they're using, but I cannot seem to find a way to do this.

---

### Post by McJuicy on 2015-08-15
So I had some dice on the command line when I "fset" the seen flag to false. Seems to work using the old value as the default value:

```
# outface
db_fset pkg/outface seen false
db_input high pkg/outface || true
db_go

# inface
db_fset pkg/inface seen false
db_input high pkg/inface || true
db_go
```

Now if I could only construct these question templates dynamically...](*,)

---

### Post by Bakerconspiracy on 2015-08-16
> **McJuicy said:**
> Now if I could only construct these question templates dynamically...](*,)

Figured it out. Put a substitution variable into the templates file ("choices" below):

```
Template: pkg/interfaces
Type: select
Choices: ${choices}
Description: .....
```

And in the config file use the db_subst to fill in the choices variable:
```
declare -a options;
count=0;

## Get interfaces from the operating system
for interface in $(ip link show | awk '/^[0-9]/ {print $2;} ' | sed 's/:$//');
do
    if [ $interface != "lo" ] && [ $interface != "" ] ;
    then
        options[$count]=$interface;
        count=$((count+1));
    fi
done

# Set the choices the user has
db_subst pkg/outface choices $options
```

---

