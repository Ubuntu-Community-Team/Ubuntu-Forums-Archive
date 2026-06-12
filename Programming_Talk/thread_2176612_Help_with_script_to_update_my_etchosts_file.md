---
title: "Help with script to update my /etc/hosts file"
date: 2013-09-25
forum: Programming Talk
---

### Post by greavette on 2013-09-25
Hello,

I have the following bash script that used to work when updating my /etc/hosts file, but now for some reason it doesn't.  


```
#!/bin/bash
#Assign existing hostname to $hostn
hostn=$(cat /etc/hostname)

#Display existing hostname
echo "Existing hostname is $hostn"

#Ask for new hostname $newhost
echo "Enter new hostname: "
read newhost

#change hostname in /etc/hosts & /etc/hostname
#sudo sed -i "s/$hostn/$newhost/g" /etc/hosts
sudo sed -i "s/$hostn/$newhost/g" /etc/hostname

cat<<EOF > /etc/hosts
# This file is automatically genreated by ec2-hostname script
127.0.0.1 localhost
127.0.0.1 $newhost
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
EOF

#display new hostname
echo "Your new hostname is $newhost"

#Press a key to reboot
read -s -n 1 -p "Press any key to reboot"
sudo shutdown -r now

```

When I execute this script my /etc/hostname is updated without any problems, but I receive a Permission Denied on the part that updates my /etc/hosts.  

I tried adding my user to visudo:

username ALL=(ALL) NOPASSWD: /path/to/hostnameupdate.sh

But this doesn't appear to have helped.

Any help on what I'm doing wrong would be greatly appreciated.

Thank you.

---

### Post by TheFu on 2013-09-25
Remove the '$'  except inside your script. This is a reserved character in regex (meaning end-of-line), so using it for any other purpose will cause hardships.  I'd make lots of other suggestions around scripting too - like use uppercase for replacements inside templates to make those standout.

Have you considered using a CM tool just for this purpose like Ansible?  I'm happy to post my common_etc_hosts.yml task file, if that helps. There's a nice introduction video and after that, you can probably start managing 1 to 100 hosts with ansible in 30 minutes.  "Manage" doesn't mean just /etc/hosts either.

---

### Post by Vaphell on 2013-09-25
> Remove the '$' except inside your script. This is a reserved character in regex (meaning end-of-line), so using it for any other purpose will cause hardships. I'd make lots of other suggestions around scripting too - like use uppercase for replacements inside templates to make those standout.

if you mean sed then it won't see any $ sign as variables will get expanded by the shell before it gets its hands on the expression.

cat > /etc/hosts doesn't look like having rights.
OP, why don't you execute your script as a whole with sudo? It will be cleaner than invoking sudo every other line.

---

### Post by TheFu on 2013-09-25
No, actually I meant this line:
```
127.0.0.1 $newhost
```

I'd have it like this:
```
127.0.0.1 REPLACE_HOSTNAME
```

Then I'd use ```

cp /etc/hosts /etc/hosts.`date +"%Y%m%d%H%M%S"` 
cat /etc/hosts | /bin/sed -e 's/REPLACE_HOSTNAME/$newhost/' > /etc/hosts
```

if I had to use shell scripting for this.  However, unless this is a secure environment where bringing in new software isn't allowed, then I'd look at using Ansible to manage more than just a simple /etc/hosts, but it can do that as well.

---

### Post by Vaphell on 2013-09-25
that form of heredoc also expands $variable so there is no dangling $ sign left. It would be a different story if the delimiter word was quoted (=no expansions)

---

### Post by greavette on 2013-09-25
I'm looking to execute this script from my openbox menu.  I'm not sure how I would execute this entire script as a whole from sudo from the menu?  The script will be run by team leads and managers from the menu when a new Thin Client is dropped into a workstation so I'd rather not run this script from the terminal using sudo...they wouldn't know what to do.

Would you know how I could execute this entire script from openbox menu using sudo privileges?

Thanks.

---

### Post by Vaphell on 2013-09-25
won't the script ask for password either way? Where is the difference?

What does your menu entry look like? can't you put sudo in front of the command to execute?

---

### Post by greavette on 2013-09-25
Even if I put sudo in front of the script I still get the permission denied message.  I've taken out the sudo in my script and used sudo to execute the script and same problem.  Crazy!

Does it look like my script should work with what I'm doing?  

Thanks.

---

### Post by Vaphell on 2013-09-25
i did run the relevant parts of the script with sudo on one of my virtualized ubuntus and it worked fine
what is the exact error message and what does *ls -l /etc/hosts* say?

---

