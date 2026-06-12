---
title: "Need help understanding responses in bash"
date: 2011-02-18
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-02-18
Hello everyone, 

I coded my own script to install ssmtp and configure it, but i am not really satisfied. 

I want my script to ask me whether i want to install certain packages. So before it reads "sudo apt-get install ssmtp" -  I want it to ask me. Can anyone help me? 

Here is my code. 


#!/bin/bash

if [ "$(/usr/bin/id -u)" != "0" ]; then
   exec /usr/bin/sudo "$0"
fi

echo "Welcome to sTaTiC's gmail setup..."

echo "Installing SSMTP..."

sudo apt-get install ssmtp

[[ $? -eq 0 ]] || { echo "Failed to install SSMTP, exiting..."; exit 1; }

echo "SSMTP installation complete!"

echo "Installing heirloom-mailx..."

sudo apt-get install heirloom-mailx

[[ $? -eq 0 ]] || { echo "Failed to install heirloom-mailx, exiting..."; exit 1; }

echo "heirloom-mailx installation complete!"

echo "configuring ssmtp.conf..."

[[ -e /etc/ssmtp/ssmtp.conf ]] && cp /etc/ssmtp/ssmtp{.conf,.bak}

[[ $? -eq 0 ]] || { echo "Failed to create backup /etc/ssmtp/ssmtp.conf, exiting..."; exit 1; }

cat <<EOF > /etc/ssmtp/ssmtp.conf
AuthUser=email@googlemail.com
AuthPass=password
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF

[[ $? -eq 0 ]] || { echo "Failed to create backup /etc/ssmtp/ssmtp.conf, exiting..."; exit 1; }

echo "Installed and configured ssmtp and heirloom-mailx"

exit

---

### Post by hakermania on 2011-02-19
```
echo "Do you want to install this?"
read YN
if [ X"$YN" = X"y" -o X"$YN" = X"Y" ]; then
apt-get install package
else
echo "Skipping package......"
fi
```

---

### Post by sisco311 on 2011-02-19
In bash you can do something like:
```

read -n1 -p "Install package foo? [Y/n] " REPLY
echo
REPLY=${REPLY:=Y}     
if [[ $REPLY = [Yy] ]]; then
  apt-get install foo || { echo "error..."; exit 1; } **>&2**
fi
```

---

