---
title: "PLEASE HELP!! Trouble installing KRoC!!!"
date: 2008-12-23
forum: Packaging and Compiling Programs
---

### Post by mcweaver1 on 2008-12-23
I need to set up KRoC so I can compile Occam programs and have been having a few issues....

Firstly I had to edit the .bashrc file, and I put in these commands: 

export PATH=:/usr/local/kroc140/bin:$PATH
export OCSEARCH=/usr/local/kroc140/lib
export KROC=/usr/local/kroc140
export MANPATH=:/usr/local/kroc140/doc:$MANPATH

I also discovered that I had no bash_profile file so I created one and put in the line: source ~/.bashrc

When I put source ~/.bashrc and source ~/.bash_profile in the terminal I don't get any messages saying no such file or directory, so I'm assuming they can be found and work correctly.

I have now followed all the instructions I was given but when I try and compile an Occam program I just get the message "bash: kroc: command not found".

How can I finish setting up the compiler??? Please help, I'm sure there's something simple I'm missing but I've been trying to sort this for a few days and haven't managed it yet....

Thanks!!!

---

