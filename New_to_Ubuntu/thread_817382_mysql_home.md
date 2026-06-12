---
title: "mysql_home"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by anderskitson on 2008-06-03
I need to run a command from terminal, that wants me to navigate to my mysql_home directory. I installed mysql from synaptic manager, and have looked at the installed files but there is so many i am not sure as to which one is the home directory, any help would be great, and I would prefer to have had mysql in usr/local if that is still possible

---

### Post by HalPomeranz on 2008-06-03
I'm guessing that mysql_home is referring to the /var/lib/mysql directory where the data files end up (and which is also set as the $HOME directory for the mysql user).  It's possible that they mean the /etc/mysql directory where the config files live.  What exactly are the instructions telling you to do once you get into mysql_home?

As for installing MySQL under /usr/local, you would need to build you own copy from source code to do that.  The default Ubuntu packages use the directories described above and put the binaries and such under /usr.

---

### Post by anderskitson on 2008-06-03
>   In a Command Prompt window, enter cd {mysql_home} to go to your 1MySQL
  home directory.
  Note: mysql_home is defined in the deploy.properties file. 
  Example: cd C:\mysql
2 Enter cd bin to go to the bin directory.
3 Enter mysql to execute the MySQL monitor.
4 Enter select * from {schema_name}.{table_name};.
  Notes:
  &#8226; schema_name is defined in the deploy.properties file.
      Example: cacore
  &#8226;   The semi-colon is an important part of the command--it prompts its execution.
5 For the initial example, enter select * from cacore.gene where gene_symbol
  like &#8216;IL%&#8217;;. There should be 9 rows displayed.
]
The mysql home does not seem to be defined in the deploy.properties file, but if it was it wouldn't be correct anyways, because this is the the deploy.properties file that came with the program. Its the sdk, so it has been build succesfuly I am just trying to view the example files that came with it on the localhost server, I am just testing now.
Mind you the instructions are for windows, but they say just to adapt them to linux. thanks for the reply

---

### Post by HalPomeranz on 2008-06-03
Ah, I see.

On Linux, just run mysql to open up the interactive MySQL console.  You don't need to cd to any particular directory because the mysql command should already be in your seach path (unlike Windows).

However a password is usually required.  I can't recall how Ubuntu sets up the default MySQL access passwords, but it's possible that you'll need to do "sudo mysql" to access the database.  Try it without the sudo first though.

---

### Post by anderskitson on 2008-06-03
i see thanks, mysql -uroot -p, works

---

