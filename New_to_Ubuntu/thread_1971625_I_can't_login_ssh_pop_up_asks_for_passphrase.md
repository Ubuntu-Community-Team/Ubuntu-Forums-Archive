---
title: "I can't login: ssh pop up asks for passphrase"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by shotgeist on 2012-05-02
I was setting up git with a ssh key passphrase on Ubuntu 12.04 via the terminal with the assistance of [Help.GitHub]("http://help.github.com/ssh-key-passphrases/"):  "You can run ssh-agent automatically when you open bash by adding the  following to your ~/.profile or ~/.bashrc file"  I added the ~/.bashrc  file:

[ALSO: have no idea why this code box is so horizontal and so not vertical: the code that I added can be viewed nicely at the Help.Github link above]
```
SSH_ENV="$HOME/.ssh/environment"  # start the ssh-agent function start_agent {     echo "Initializing new SSH agent..."     # spawn ssh-agent     ssh-agent | sed 's/^echo/#echo/' > "$SSH_ENV"     echo succeeded     chmod 600 "$SSH_ENV"     . "$SSH_ENV" > /dev/null     ssh-add }  # test for identities function test_identities {     # test whether standard identities have been added to the agent already     ssh-add -l | grep "The agent has no identities" > /dev/null     if [ $? -eq 0 ]; then         ssh-add         # $SSH_AUTH_SOCK broken so we start a new proper agent         if [ $? -eq 2 ];then             start_agent         fi     fi }  # check for running ssh-agent with proper $SSH_AGENT_PID if [ -n "$SSH_AGENT_PID" ]; then     ps -ef | grep "$SSH_AGENT_PID" | grep ssh-agent > /dev/null     if [ $? -eq 0 ]; then     test_identities     fi # if $SSH_AGENT_PID is not properly set, we might be able to load one from # $SSH_ENV else     if [ -f "$SSH_ENV" ]; then     . "$SSH_ENV" > /dev/null     fi     ps -ef | grep "$SSH_AGENT_PID" | grep -v grep | grep ssh-agent > /dev/null     if [ $? -eq 0 ]; then         test_identities     else         start_agent     fi fi
```
A little later I restarted my computer.  Now, whenever I attempt to  log on (i.e. enter my password and press enter at the login screen) as  the sole user (as opposed to guest) the screen goes black and a pop-up  appears asking me for my /.ssh/rsa_id passphrase.

  
  When I enter the passphrase I entered for GitHub, Ubuntu throws me  back to the login screen, square one. The only way I know how else to  login functionally is as a guest.  
  

What has happened and what can I do to fix this?

---

### Post by Peter09 on 2012-05-03
To get back into your account you can:
 
Hold the shift key while the system boots, this should get you into a startup screen, select the recovery prompt.
 
When that gets to a menu select the root prompt with network option. You can then navigate to your home directory using the command
 
```
 
cd /home/<your username>

```
 
edit the file that you setup using
 
```
 
nano <filename>

```
 
 
Then reboot and hopefully you should be able to login.

---

