---
title: "BASH script experience"
date: 2019-10-03
forum: Programming Talk
---

### Post by jessica-0 on 2019-10-03
Good morning all,
  First off, my name is Jessica, I have been a user of many Linux flavors for many many many, ok way too many's of years. I was tasked at work for this little script that will allow a user to empty a file simply by typing: `empty filename.ext` and it would do the same thing as cat /dev/null > filename. Then it turned into, allow them to have make a backup of the file just in case... So I added -b. Then they forgot the -b argument, so I added a -h. Then people started using this as root... AGGHHH!!! So I added a check to see if the EUID was 0 and, well yeah I think you are starting to grasp the idea, the people I work with are great, the management are idiots.

  Now that I have everyone attention, or lost them due to my lack of retention skills, I thought I would get opinions, improvements, critics, and bashing (ha ha see what I did there!) I do realize this is probably the stupidest thing ever but for fun I wanted to REALLY go all out and see what falls from it.

  Although I have combined all of this is 1 script here, they are in actually 3 different files. .bashrc, which contains all of the Colors and sources the other 2 files, .bash_functions which contain all of the functions, including this empty() function, and .bash_commands, just a simple help file for reference. Also a quick note, I have the log files saving to ~/.local/logs

```



[COLOR=#d4d4d4][FONT=Consolas][COLOR=#d4d4d4][FONT=Consolas]
[COLOR=#d4d4d4][FONT=Consolas][COLOR=#6a9955]# Define colors[/COLOR]
[COLOR=#d4d4d4]NOCOLOR=[/COLOR][COLOR=#ce9178]"\033[0m"[/COLOR]
[COLOR=#d4d4d4]BLACK=[/COLOR][COLOR=#ce9178]"\033[0;30m"[/COLOR]
[COLOR=#d4d4d4]RED=[/COLOR][COLOR=#ce9178]"\033[0;31m"[/COLOR]
[COLOR=#d4d4d4]GREEN=[/COLOR][COLOR=#ce9178]"\033[0;32m"[/COLOR]
[COLOR=#d4d4d4]BROWN=[/COLOR][COLOR=#ce9178]"\033[0;33m"[/COLOR]
[COLOR=#d4d4d4]BLUE=[/COLOR][COLOR=#ce9178]"\033[0;34m"[/COLOR]
[COLOR=#d4d4d4]MAGENTA=[/COLOR][COLOR=#ce9178]"\033[0;35m"[/COLOR]
[COLOR=#d4d4d4]CYAN=[/COLOR][COLOR=#ce9178]"\033[0;36m"[/COLOR]
[COLOR=#d4d4d4]GRAY=[/COLOR][COLOR=#ce9178]"\033[0;37m"[/COLOR]
[COLOR=#d4d4d4]DARKGRAY=[/COLOR][COLOR=#ce9178]"\033[1;30m"[/COLOR]
[COLOR=#d4d4d4]LIGHTRED=[/COLOR][COLOR=#ce9178]"\033[1;31m"[/COLOR]
[COLOR=#d4d4d4]LIGHTGREEN=[/COLOR][COLOR=#ce9178]"\033[1;32m"[/COLOR]
[COLOR=#d4d4d4]YELLOW=[/COLOR][COLOR=#ce9178]"\033[1;33m"[/COLOR]
[COLOR=#d4d4d4]LIGHTBLUE=[/COLOR][COLOR=#ce9178]"\033[1;34m"[/COLOR]
[COLOR=#d4d4d4]LIGHTMAGENTA=[/COLOR][COLOR=#ce9178]"\033[1;35m"[/COLOR]
[COLOR=#d4d4d4]LIGHTCYAN=[/COLOR][COLOR=#ce9178]"\033[1;36m"[/COLOR]
[COLOR=#d4d4d4]WHITE=[/COLOR][COLOR=#ce9178]"\033[1;37m"[/COLOR]

[/FONT][/COLOR]
[COLOR=#dcdcaa]
empty[/COLOR][COLOR=#d4d4d4]() {[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# ENVIRONMENT: BASH[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# SCOPE: To remove all contents of a file with proper error handeling and backup options[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# USAGE: empty [-b] [-h] {path}/filename.ext[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]#[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Still in development[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]#   1. Order of parameters and filename: i.e. empty test.txt -b (-b reports as the filename[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]#   2. Multiple file handling[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]#   3. Not sure how to fix just yet[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]#       a. if someone empties a file in the same path they are currently working in the log file reports ./filename[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]#          it should give the FQPN[/COLOR]

[COLOR=#d4d4d4]  [/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Set all variables to local function and default the filename to the $1[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] OPTIND[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] arguments=[/COLOR][COLOR=#ce9178]""[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] superuser=[/COLOR][COLOR=#ce9178]"0"[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] logfile=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${HOME}[/COLOR][COLOR=#ce9178]/.local/logs/empty_$(date '+%F_%H%M%S').log"[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] environment=[/COLOR][COLOR=#ce9178]"DEBUG"[/COLOR]
[COLOR=#d4d4d4]  [/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - Empty Function Log File Begin"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Create a debug file with line numbers for xtrace[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#9cdcfe]$environment[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]==[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"DEBUG"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]exec[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]5>[/COLOR][COLOR=#d4d4d4] debug__[/COLOR][COLOR=#ce9178]$(date '+%F_%H%M%S')[/COLOR][COLOR=#d4d4d4].log[/COLOR]
[COLOR=#d4d4d4]    BASH_XTRACEFD=[/COLOR][COLOR=#ce9178]"5"[/COLOR]
[COLOR=#d4d4d4]    PS4=[/COLOR][COLOR=#ce9178]'$LINENO: '[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]set[/COLOR][COLOR=#d4d4d4] -x[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]fi[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# If the user is root or super then set the value to 1[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [ [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$EUID[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]-eq[/COLOR][COLOR=#d4d4d4] 0 ][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]    superuser=[/COLOR][COLOR=#ce9178]"1"[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#6a9955]# Add into log file an elevated user is running this script[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - Elevated user"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]fi[/COLOR]


[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Do some basic checking to see if $1 is null or empty, it shouldn't be[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]![/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$1[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#6a9955]# Just in case $1 is a filename, let's break it up so we can have the variables needed for the path, filename, and extension[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] filename=[/COLOR][COLOR=#ce9178]$(basename -- "[/COLOR][COLOR=#9cdcfe]$1[/COLOR][COLOR=#ce9178]")[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] base=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${filename[/COLOR][COLOR=#d4d4d4]%[/COLOR][COLOR=#9cdcfe].[^.][/COLOR][COLOR=#d4d4d4]*[/COLOR][COLOR=#9cdcfe]}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] path=[/COLOR][COLOR=#ce9178]"$(dirname -- [/COLOR][COLOR=#9cdcfe]$1[/COLOR][COLOR=#ce9178])/"[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] extension=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${filename[/COLOR][COLOR=#d4d4d4]:[/COLOR][COLOR=#9cdcfe]${[/COLOR][COLOR=#d4d4d4]#[/COLOR][COLOR=#9cdcfe]base} + 1}[/COLOR][COLOR=#ce9178]"[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#569cd6]local[/COLOR][COLOR=#d4d4d4] filename=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${filename[/COLOR][COLOR=#d4d4d4]%%[/COLOR][COLOR=#9cdcfe].[/COLOR][COLOR=#d4d4d4]*[/COLOR][COLOR=#9cdcfe]}[/COLOR][COLOR=#ce9178]"[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$base[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]&&[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]-n[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]      base=[/COLOR][COLOR=#ce9178]".[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]      extension=[/COLOR][COLOR=#ce9178]""[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]elif[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]![/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]

[COLOR=#d4d4d4]      base=[/COLOR][COLOR=#ce9178]""[/COLOR]

[COLOR=#d4d4d4]      extension=[/COLOR][COLOR=#ce9178]".[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]fi[/COLOR]
[COLOR=#d4d4d4]  [/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Since $1 was empty, then no parameters (like -h) or filename was specified.[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]else[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"\nNo file was specified to empty. Use [/COLOR][COLOR=#9cdcfe]${BRIGHTRED}[/COLOR][COLOR=#ce9178]empty -h[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178] for help.\n"[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]return[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]fi[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Check if $1 has the -b or -h arguments, if it doesn't it should be a filename[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]while[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]getopts[/COLOR][COLOR=#d4d4d4] :bh arguments[/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]do[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]case[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$arguments[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]in[/COLOR]
[COLOR=#d4d4d4]      b) [/COLOR][COLOR=#6a9955]# backup contents of file to a backup file[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# Since -b was invoked, $1 now contains the -b, so the new variable should be $2 and reset[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# all of the variables to reflect the new variable[/COLOR]
[COLOR=#d4d4d4]        filename=[/COLOR][COLOR=#ce9178]$(basename -- "[/COLOR][COLOR=#9cdcfe]$2[/COLOR][COLOR=#ce9178]")[/COLOR]
[COLOR=#d4d4d4]        path=[/COLOR][COLOR=#ce9178]"$(dirname -- [/COLOR][COLOR=#9cdcfe]$2[/COLOR][COLOR=#ce9178])/"[/COLOR]
[COLOR=#d4d4d4]        base=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${filename[/COLOR][COLOR=#d4d4d4]%[/COLOR][COLOR=#9cdcfe].[^.][/COLOR][COLOR=#d4d4d4]*[/COLOR][COLOR=#9cdcfe]}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]        extension=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${filename[/COLOR][COLOR=#d4d4d4]:[/COLOR][COLOR=#9cdcfe]${[/COLOR][COLOR=#d4d4d4]#[/COLOR][COLOR=#9cdcfe]base} + 1}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]        filename=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${filename[/COLOR][COLOR=#d4d4d4]%%[/COLOR][COLOR=#9cdcfe].[/COLOR][COLOR=#d4d4d4]*[/COLOR][COLOR=#9cdcfe]}[/COLOR][COLOR=#ce9178]"[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$base[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]&&[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]-n[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]

[COLOR=#d4d4d4]          base=[/COLOR][COLOR=#ce9178]".[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]          extension=[/COLOR][COLOR=#ce9178]""[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]elif[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]![/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]          base=[/COLOR][COLOR=#ce9178]""[/COLOR]
[COLOR=#d4d4d4]          extension=[/COLOR][COLOR=#ce9178]".[/COLOR][COLOR=#9cdcfe]$extension[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]fi[/COLOR]


[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# Copy the filename and add the current date and time with the extension if there was one[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]-f[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]          newfile=[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${path}${filename}[/COLOR][COLOR=#ce9178]_$(date '+%F_%H%M%S')[/COLOR][COLOR=#9cdcfe]${extension}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]          cp [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$newfile[/COLOR]
[COLOR=#d4d4d4]          [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - File backup [/COLOR][COLOR=#9cdcfe]${newfile}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]else[/COLOR]

[COLOR=#d4d4d4]          [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"Filename [/COLOR][COLOR=#9cdcfe]${LIGHTRED}${path}${filename}${extension}${NOCOLOR}[/COLOR][COLOR=#ce9178] could not be found."[/COLOR]

[COLOR=#d4d4d4]          [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - File was not found [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]
[COLOR=#d4d4d4]          OPTIND=0[/COLOR]
[COLOR=#d4d4d4]          [/COLOR][COLOR=#c586c0]return[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]fi[/COLOR]

[COLOR=#d4d4d4]        OPTIND=0[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]break[/COLOR][COLOR=#d4d4d4];;[/COLOR]

[COLOR=#d4d4d4]      h) [/COLOR][COLOR=#6a9955]# help[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# Since -h was invoked, nothing should run after that, show the help and use return instead[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# of exit to maintain the shell window to stay open. Reset the OPTIND to 0[/COLOR]
[COLOR=#d4d4d4]        commands empty[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - Help was executed"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]
[COLOR=#d4d4d4]        OPTIND=0[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]return[/COLOR][COLOR=#d4d4d4];;[/COLOR]

[COLOR=#d4d4d4]      [/COLOR][COLOR=#d7ba7d]\?[/COLOR][COLOR=#d4d4d4]) [/COLOR][COLOR=#6a9955]# Testing for invalid options (anything other then -h -b)[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTRED}[/COLOR][COLOR=#ce9178]Invalid option: [/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]-[/COLOR][COLOR=#9cdcfe]${arguments}${NOCOLOR}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - Invalid option was given [/COLOR][COLOR=#9cdcfe]${arguments}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]
[COLOR=#d4d4d4]        OPTIND=0[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]return[/COLOR][COLOR=#d4d4d4];;[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]esac[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]done[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Checking to see if the filename was entered[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"\nNo file was specified to empty. Use [/COLOR][COLOR=#9cdcfe]${BRIGHTRED}[/COLOR][COLOR=#ce9178]empty -h[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178] for help.\n"[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - No file was specified"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]else[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#6a9955]# Checking to see if the filename exists in the path[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#d4d4d4]-f[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]      [/COLOR][COLOR=#6a9955]# Checking to see if super user or root is the user[/COLOR]
[COLOR=#d4d4d4]      [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#9cdcfe]$superuser[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]==[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"1"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTRED}[/COLOR][COLOR=#ce9178]WARNING: [/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]You are about to remove a file with super user priviledges."[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]If you are aware of the risks, press Y to continue."[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]read[/COLOR][COLOR=#d4d4d4] warning[/COLOR]


[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# If the super user is aware of the risks, and would like to continue, then press Y[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#9cdcfe]$warning[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]==[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"Y"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]||[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$warning[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]==[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"y"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]          [/COLOR][COLOR=#6a9955]# Ok, here we go with elevated priviledges[/COLOR]
[COLOR=#d4d4d4]          cat /dev/null [/COLOR][COLOR=#d4d4d4]>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR]
[COLOR=#d4d4d4]          [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - Elevated user executed the empty [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]else[/COLOR]

[COLOR=#d4d4d4]          [/COLOR][COLOR=#6a9955]# Good choice on desclating your priviledge[/COLOR]
[COLOR=#d4d4d4]          [/COLOR][COLOR=#c586c0]return[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]fi[/COLOR]
[COLOR=#d4d4d4]      [/COLOR][COLOR=#c586c0]else[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#6a9955]# So the filename exists, the user wasn't super, just do it![/COLOR]
[COLOR=#d4d4d4]        cat /dev/null [/COLOR][COLOR=#d4d4d4]>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#ce9178] was successfully emptied"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]

[COLOR=#d4d4d4]      [/COLOR][COLOR=#c586c0]fi[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]else[/COLOR]
[COLOR=#d4d4d4]      [/COLOR][COLOR=#6a9955]# So the filename couldn't be found, let safely let them know[/COLOR]
[COLOR=#d4d4d4]      [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"Filename [/COLOR][COLOR=#9cdcfe]${LIGHTRED}${path}${filename}${extension}${NOCOLOR}[/COLOR][COLOR=#ce9178] could not be found."[/COLOR]
[COLOR=#d4d4d4]      [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[$(date '+%H%M%S')] - File was not found [/COLOR][COLOR=#9cdcfe]${path}${filename}${extension}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]>>[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$logfile[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]fi[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]fi[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#6a9955]# Reset the OPTIND to 0[/COLOR]
[COLOR=#d4d4d4]  OPTIND=0[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [[ [/COLOR][COLOR=#9cdcfe]$environment[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#d4d4d4]==[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"DEBUG"[/COLOR][COLOR=#d4d4d4] ]][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]set[/COLOR][COLOR=#d4d4d4] +x[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]fi[/COLOR]

[COLOR=#d4d4d4]}[/COLOR]

[/FONT][/COLOR]
[COLOR=#dcdcaa]
commands[/COLOR][COLOR=#d4d4d4]() {[/COLOR]

[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [ [/COLOR][COLOR=#d4d4d4]-z[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$1[/COLOR][COLOR=#d4d4d4] ][/COLOR][COLOR=#d4d4d4];[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]then[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"All Commends"[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]else[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]case[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$1[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#c586c0]in[/COLOR]

[COLOR=#d4d4d4]      empty)[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"\n\n[/COLOR][COLOR=#9cdcfe]${LIGHTRED}${LINE}${NOCOLOR}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTCYAN}[/COLOR][COLOR=#ce9178]EMPTY[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178] {parameters}:"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    Remove all contents of a file without changing permissions. Unless specified,"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    no backup of the file will be made.\n\n"[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]USAGE[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]:"[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    [/COLOR][COLOR=#9cdcfe]${YELLOW}[/COLOR][COLOR=#ce9178]empty [/COLOR][COLOR=#9cdcfe]${DARKGRAY}[/COLOR][COLOR=#ce9178][[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]-b[/COLOR][COLOR=#9cdcfe]${DARKGRAY}[/COLOR][COLOR=#ce9178]] [/COLOR][COLOR=#9cdcfe]${DARKGRAY}[/COLOR][COLOR=#ce9178][[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]-h[/COLOR][COLOR=#9cdcfe]${DARKGRAY}[/COLOR][COLOR=#ce9178]] [/COLOR][COLOR=#9cdcfe]${LIGHTCYAN}[/COLOR][COLOR=#ce9178]/path/[/COLOR][COLOR=#9cdcfe]${LIGHTMAGENTA}[/COLOR][COLOR=#ce9178]filename.ext[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]\n\n"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]PARAMETERS[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]:"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    [/COLOR][COLOR=#9cdcfe]${WHITE}[/COLOR][COLOR=#ce9178]-b      [/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]Backup contents of the file by copying the data to [/COLOR][COLOR=#9cdcfe]${LIGHTMAGENTA}[/COLOR][COLOR=#ce9178]filename_datetime.ext[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]."[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    [/COLOR][COLOR=#9cdcfe]${WHITE}[/COLOR][COLOR=#ce9178]-h      [/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]Displays detailed information about this command."[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTRED}${LINE}${NOCOLOR}[/COLOR][COLOR=#ce9178]\n\n"[/COLOR]
[COLOR=#d4d4d4]      ;;[/COLOR]

[COLOR=#d4d4d4]      help)[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"\n\n[/COLOR][COLOR=#9cdcfe]${LIGHTRED}${LINE}${NOCOLOR}[/COLOR][COLOR=#ce9178]"[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTCYAN}[/COLOR][COLOR=#ce9178]HELP[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178] {topic}:"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    This help file will show all custom made functions that are available with the"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    bash_functions file installed with this BASH Start Up script.\n\n"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]USAGE[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]:"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    [/COLOR][COLOR=#9cdcfe]${YELLOW}[/COLOR][COLOR=#ce9178]commands [/COLOR][COLOR=#9cdcfe]${DARKGRAY}[/COLOR][COLOR=#ce9178][[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]help topic[/COLOR][COLOR=#9cdcfe]${DARKGRAY}[/COLOR][COLOR=#ce9178]][/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]\n\n"[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTGREEN}[/COLOR][COLOR=#ce9178]HELP TOPICS[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]:"[/COLOR]

[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"    [/COLOR][COLOR=#9cdcfe]${WHITE}[/COLOR][COLOR=#ce9178]empty      [/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]to quickly empty a file without loosing permissions, and to have an optional backup of the contents"[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTRED}${LINE}${NOCOLOR}[/COLOR][COLOR=#ce9178]\n\n"[/COLOR]
[COLOR=#d4d4d4]      ;;[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]esac[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]fi[/COLOR]
[COLOR=#d4d4d4]  [/COLOR][COLOR=#c586c0]return[/COLOR][COLOR=#d4d4d4] 0[/COLOR]

[COLOR=#d4d4d4]}[/COLOR]

[/FONT][/COLOR]


```

---

### Post by sudodus on 2019-10-03
Welcome to the Ubuntu Forums Jessica :-)

The command line
```

cat /dev/null > file

```
creates a file with zero length without overwriting the data on the disk.

This is what you suggest. Is it doing what you want?

In that case
```

> file

```
will do it too (and simpler).

[hr][/hr]
- How is that file used? I am asking because in most cases but not always files need not be emptied, only deleted or overwritten. Is the content confidential? Must the file have a fixed size? Must it be zeroised?

- Is the backup in the same partition or in another partition or even another computer, for example a file server? If in the same partition the **mv** command would be instant (much faster than copying).

- The fastest way to create a file in a Linux system is using **fallocate**, for example

```

fallocate -l 50G file 

```

according to [the accepted answer at this link](https://unix.stackexchange.com/questions/292843/way-to-instantly-fill-up-use-up-lots-of-disk-space)

- But maybe the file is small, so that there is no problem to wait for copying and overwriting or you need overwriting with zeros. In that case I would suggest that you use **dd**, as in the example below to create a file with size 1 Gibibyte,

```

dd if=/dev/zero of=file bs=1M count=1k

```

- Please notice the difference between
```

cat /dev/null > file

```
that creates a file with zero length without overwriting anything,

and
```

cat /dev/zero > file

```
that continues to write until you interrupt it or the file system is full.

[hr][/hr]
For maintenance reasons, I suggest that you put the whole task into one single file, a bash shellscript file starting with the shebang

```

#!/bin/bash

```

and make functions within the shellscripts for each task to make things easier to read for debugging and future development.

It is easier to distribute one shellscript to the users than to distribute several chunks in different files.

---

### Post by jessica-0 on 2019-10-03
[COLOR="#000000"]> **sudodus said:**
> Welcome to the Ubuntu Forums Jessica :-)

The command line
```

cat /dev/null > file

```
creates a file with zero length without overwriting the data on the disk.

This is what you suggest. Is it doing what you want?

In that case
```

> file

```
will do it too (and simpler).

[HR][/HR]

[COLOR=#ff0000]So I am not 100% sure what you are referring to on the above comment. But maybe by me answering your questions below will make more sense. I want to confirm you are saying
[/COLOR]```

cat > file
# or
/dev/null > file
# or
> file

```

> **sudodus said:**
> 
- How is that file used? I am asking because in most cases but not always files need not be emptied, only deleted or overwritten. Is the content confidential? Must the file have a fixed size? Must it be zeroised?


[COLOR=#ff0000]So let me explain that this isn't a separate file. This is a function that I created in this very elaborate .bashrc file. To explain in further, I am doing this inside the .bashrc file

[/COLOR]```

[COLOR=#d4d4d4][FONT=Consolas][COLOR=#6a9955]# open and source BASH files if the file exists[/COLOR]

[COLOR=#d4d4d4]FILES=([/COLOR][COLOR=#ce9178]".bash_functions"[/COLOR][COLOR=#ce9178] ".bash_aliases"[/COLOR][COLOR=#ce9178] ".bash_exports" [/COLOR][COLOR=#ce9178]".bash_custom_commands"[/COLOR][COLOR=#d4d4d4])[/COLOR]

[COLOR=#c586c0]for[/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#c586c0]in[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${FILES[@]}[/COLOR][COLOR=#ce9178]"[/COLOR]
[COLOR=#c586c0]do[/COLOR]
[COLOR=#d4d4d4]   [[ [/COLOR][COLOR=#d4d4d4]-f[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${HOME}[/COLOR][COLOR=#ce9178]/[/COLOR][COLOR=#9cdcfe]${i}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4] ]] [/COLOR][COLOR=#d4d4d4]&&[/COLOR][COLOR=#dcdcaa].[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${HOME}[/COLOR][COLOR=#ce9178]/[/COLOR][COLOR=#9cdcfe]${i}[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4]||[/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] -e [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]${LIGHTRED}[/COLOR][COLOR=#ce9178]BASH resource file [/COLOR][COLOR=#9cdcfe]${LIGHTBLUE}[/COLOR][COLOR=#ce9178]([/COLOR][COLOR=#9cdcfe]${LIGHTCYAN}${i}${LIGHTBLUE}[/COLOR][COLOR=#ce9178]) [/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]was not found in [/COLOR][COLOR=#9cdcfe]${YELLOW}${HOME}[/COLOR][COLOR=#9cdcfe]${NOCOLOR}[/COLOR][COLOR=#ce9178]folder, failed to load the file."[/COLOR]
[COLOR=#c586c0]done[/COLOR][/FONT][/COLOR]

```
[COLOR=#ff0000]
The function empty is inside the .bash_functions file along with many other functions that I have created for people that just will not learn Linux properly, or to make several commands into one.
The commands function is inside the .bash_custom_commands file for a central location of all of the help commands for the functions inside the .bash_functions and the aliases in the .bash_aliases
All of the variables (like the colors) are inside the .bashrc file.[/COLOR]

> **sudodus said:**
> 
- Is the backup in the same partition or in another partition or even another computer, for example a file server? If in the same partition the **mv** command would be instant (much faster than copying).


[COLOR=#ff0000]So lets say you have a file that just has a bunch of junk in it (about 50 - 100 lines of text) called test.sh and you have applied chmod +x to the file, and you just want to empty the file, but just in case you want to backup the contents you throw the -b to the empty command. To execute this process it would be: empty -b test.sh it will then copy the file from test.sh to test_20191003_162418.sh then cat /dev/null > test.sh. This will retain the +x on the file and the file will have all lines of the file emptied with all of the data that was in test.sh saved in a datetime stamped backup file.

I hope that explains a little more about this function.[/COLOR]

> **sudodus said:**
> 
- The fastest way to create a file in a Linux system is using **fallocate**, for example

```

fallocate -l 50G file 

```

according to [the accepted answer at this link]("https://unix.stackexchange.com/questions/292843/way-to-instantly-fill-up-use-up-lots-of-disk-space")

- But maybe the file is small, so that there is no problem to wait for copying and overwriting or you need overwriting with zeros. In that case I would suggest that you use **dd**, as in the example below to create a file with size 1 Gibibyte,

```

dd if=/dev/zero of=file bs=1M count=1k

```

- Please notice the difference between
```

cat /dev/null > file

```
that creates a file with zero length without overwriting anything,

and
```

cat /dev/zero > file

```
that continues to write until you interrupt it or the file system is full.

[HR][/HR]
For maintenance reasons, I suggest that you put the whole task into one single file, a bash shellscript file starting with the shebang

```

#!/bin/bash

```

and make functions within the shellscripts for each task to make things easier to read for debugging and future development.

It is easier to distribute one shellscript to the users than to distribute several chunks in different files.

[COLOR=#ff0000]Did my longer explanation above help explain these comments above?[/COLOR][/COLOR]

---

### Post by sudodus on 2019-10-04
I think I understand what your scripts and code snippets are doing, and what you want to do:

- the target file is small
- make the target file empty (zero length), but keep the name, ownership and permissions
- provide the option to back it up (with a time stamp in the name) before making it empty
- help the users steer away from using elevated permissions, when it is not necessary.

- I tried to say that
```

> file

```
will do what you do with the **cat** command line (and simpler, you need not involve cat and /dev/null). If I understand correctly, this is what you want, and a good shellscript should use as simple commands as possible.

- I think it is good that you have lots of comments to help maintain and develop the scripts and code snippets.

- You need not bother about my tips with command lines using fallocate and dd. They should be used for other purposes.

[hr][/hr]
- The tip after the horizontal line in my first post, to put the whole task into one single shellscript file, is optional, of course. If you are happy with the current structure, fine.

---

### Post by jessica-0 on 2019-10-04
Thank you for your information, it has given me a little more to think about. I agree about the file size, or the data type. What happens if the file is 5GB in size, and they need to create another padded 5GB file. I think I am thinking way too much about this, and I shouldn't be programming every possible feature for every possible need. This could cause more security issues and more bugs to fix. 

I noticed that this forum is stripping some spaces when I paste code. I am not sure if VS Code is doing that, or if the forum, nevertheless I will worry about that the next time I paste something.

---

### Post by TheFu on 2019-10-04
**Sometimes telling management "no" is the best answer.**  Either they trust your expertise and the normal system users or they don't.
IMO, scripting stuff like this is a waste of your time and the time for all the users.  Post the simple command in the daily login message and leave it at that. After some period, remove the message.  

 I still see so many books showing 
```
cat file | grep "something"
```
Those book authors need to be paddled.  Think of all the wasted CPU/pipes caused because people think grep can't actually use file globbing?  I have much more use for **tac** than I've ever had for **cat**.  I can think of 1 time where I needed cat in the last 10 yrs or so.

---

### Post by sudodus on 2019-10-04
> **jessica-0 said:**
> Thank you for your information, it has given me a little more to think about. I agree about the file size, or the data type. What happens if the file is 5GB in size, and they need to create another padded 5GB file. I think I am thinking way too much about this, and I shouldn't be programming every possible feature for every possible need. This could cause more security issues and more bugs to fix. 

I agree, you shouldn't be programming every possible feature for every possible need.
> 
I noticed that this forum is stripping some spaces when I paste code. I am not sure if VS Code is doing that, or if the forum, nevertheless I will worry about that the next time I paste something.

It depends how you copy and paste. It works well for me, when I copy/paste from a text editor, and code looks better when surrounded by [noparse][code][/noparse] tags, *but without any further formatting*:

---

