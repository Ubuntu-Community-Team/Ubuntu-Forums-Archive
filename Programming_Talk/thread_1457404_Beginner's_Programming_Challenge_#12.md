---
title: "Beginner's Programming Challenge #12"
date: 2010-04-18
forum: Programming Talk
---

### Post by falconindy on 2010-04-18
[size=5]Beginner Programming Challenge #12[/size]

Welcome to the 12th Beginner Programming Challenge! As I was selected the winner of [Challenge #11]("http://ubuntuforums.org/showthread.php?t=1441700"), I've been tasked with presenting a new challenge! 

If you need help, feel free to drop by on IRC on irc.freenode.net in #ubuntu-beginners-dev.

As many of the previous challenges have been math related, I've opted for something a little more practical. This opens up a wider variety of languages and prevents an exercise in number crunching to make some languages less desireable (im looking at you, Ruby). It **might** immediately disqualify a language or two, but I think we'll be okay.

[size=3]_Task:_[/size]
Implement a slimmed down version of the everyday command 'ls'. This may seem simple, but it's a good opportunity to write well modularized code as it's an extremely extensible task.

[size=3]_Requirements:_[/size]
[list][*]Implement, at a minimum, the following flags: -l, -a, -F, -h. If you need a description of these, consult the man page. Most languages have a library similar to getopt that should make the actual flag parsing fairly straightforward. Sorry, Luasers.
[*]Some subreqs for -l: You do not need to convert permissions to letter format. Octal is fine. Owner and group can be presented as numerical or converted to names. Columns should be fixed size so that output is neatly arranged.
[*]All output should be well formatted. This means -l output should be in fixed columns. Non -l output can be a single column, as it would look in a pipe.
[*]Allow for argument(s) to list a specific path rather than the pwd. If a directory is specified, list the contents of that directory. These arguments can be relative or absolute paths. If multiple arguments are specified, any output belonging to a directory that isn't the pwd should have a header giving the relative path. (This behavior can be seen by `ls /bin /sbin`).
[/list]

[size=3]_Extra Credit:_[/size]
[list][*]Add more flags: the more the merrier. Allow for long opts as well as short opts.
[*]Toss out the -l subreqs: Convert octal permissions to letter format: e.g. -rwxr-xr-x, and GID/UID to real names.
[*]Recursion.
[/list]

[size=3]_Caveats:_[/size]
Any entry using a call to system() or anything similar will be disqualified. The idea here is to traverse the file system using your own implementation, not someone else's.

As always:
Any overly obfuscated code will be immediately disqualified without account for programmers skill. Please remember that these challenges are for beginners and therefore the code should be _easily readable and well commented_.

Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.

Please provide instructions for how to run your program along with your submission.

And with that...
[size=4]Have fun![/size]

---

### Post by Bodsda on 2010-04-19
Sounds like a great challenge, well pitched to the level of skill for beginners. I will definately be giving this a go when I get home tonight. 
 
Bodsda

---

### Post by pokebirdd on 2010-04-19
This isn't allowed right?

[PHP]import sys, os
print os.listdir(os.getcwd())
[/PHP]

Because otherwise, I don't really understand how we can find all the files in the working directory. :confused:

---

### Post by Tony Flury on 2010-04-19
pokebirdd : even though in Python your are right - that does produce a simple list of all the files - what about the other requirements of the challenge - like the flags - and the ability to pass in a directory to be listed as a parameter. That will take a lot more code - even in python.

---

### Post by phrostbyte on 2010-04-19
You can also kind of see how "ls" is implemented by looking at its source code. It's quite complicated, at least the GNU coreutils "ls" that is bundled with Ubuntu.

---

### Post by WillFerrellLuva on 2010-04-19
Here is my 1st shot at it written in python.  Had to look a lot of stuff up for this one.  [http://docs.python.org/library/]("http://docs.python.org/library/") was my friend.  Probably will add more functionality and format the output better latter on.

```

#! /usr/bin/python
import sys, os, grp, pwd, datetime

class Command:
    def __init__(self, apath, aoptions):
        self.path = apath
        self.l = False
        self.a = False
        self.F = False
        self.h = False
        for option in aoptions:
            if option == "-l":
                self.l = True
            elif option == "-a":
                self.a = True
            elif option == "-F":
                self.F = True
            elif option == "-h":
                self.h = True

    def display(self):
        #test to see if directory exists and
        # if you are allowed to read the directory
        if os.access(self.path, os.F_OK) and os.access(self.path, os.R_OK):
            #path name is good, process options
            print self.path + ":"
            for entry in sorted(os.listdir(self.path)):
                #test whether or not to print the entry
                if entry[0] != "." or self.a:
                    #check for -l option
                    if self.l:
                        stat_info = os.stat(self.path + "/" + entry)
                        user = pwd.getpwuid(stat_info.st_uid)[0]
                        group = grp.getgrgid(stat_info.st_gid)[0]
                        time = str(datetime.date.fromtimestamp(stat_info.st_mtime))
                        size = str(stat_info.st_size)
                        #check for -h option
                        if self.h:
                            size = str(stat_info.st_size / 1024) + "KB"
                        sys.stdout.write(str(stat_info.st_mode) + " ")
                        sys.stdout.write(str(stat_info.st_nlink) + " ")
                        sys.stdout.write(user + " ")
                        sys.stdout.write(group + " ")
                        sys.stdout.write(size + " ")
                        sys.stdout.write(time + " ")
                    #write entry
                    sys.stdout.write(entry)
                    #check for F option
                    if self.F:
                        if os.path.isdir(self.path + "/" + entry):
                            sys.stdout.write("/")
                        elif os.path.islink(self.path + "/" + entry):
                            sys.stdout.write("@")
                        elif os.access(self.path + "/" + entry, os.X_OK):
                            sys.stdout.write("*")
                    print
        else:
            print "Directory " + self.path + " does not exist,",
            print "or you do not have reading privledges."

def main():
    #all commands are kept as a class in a list
    commands = []
    #set default pathname and options
    path_name = os.getcwd()
    options = []
    length = len(sys.argv)
    if length == 1:
        #no path or options given, add default command
        commands.append(Command(path_name, options))
    else:
        while True:
            #test for path or option
            if sys.argv[1][0] == "/":
                #argv[1] is a path name, now check for options
                path_name = sys.argv[1]
                del sys.argv[1]
                length -= 1
                if length == 1:
                    #there are no options, add Command
                    commands.append(Command(path_name, options))
                    break
                while sys.argv[1][0] == "-":
                    options.append(sys.argv[1])
                    del sys.argv[1]
                    length -= 1
                    if length == 1:
                        break
                #now all the options are accounted for, add Command
                commands.append(Command(path_name, options))
            elif sys.argv[1][0] == "-":
                #an option was given with no path name
                while sys.argv[1][0] == "-":
                    options.append(sys.argv[1])
                    del sys.argv[1]
                    length -= 1
                    if length == 1:
                        break
                commands.append(Command(path_name, options))
            else:
                sys.exit("Invalid entry.")
            if length == 1:
                break
    #process all of the commands
    for item in commands:
        item.display()         

if __name__ == "__main__":
    main()


```

---

### Post by lostinxlation on 2010-04-20
Perl
 
 
Exclude mine from the contest..
 
 
EDIT: Eliminated chdir and %ENV hash.
EDIT2: Fixed a bug.
 
```

#!/usr/bin/perl
 
use strict;
use warnings;
#use File::stat;
use Fcntl ':mode';
use POSIX 'strftime';
 
 
our($max_nlink, $max_uid, $max_gid, $max_size)=(0,0,0,0);
our(%type, %exec, %perm, %nlink, %username, %groupname, %modtime, %filesize, %filename);
 
my(@x, @arg);
my($l, $F, $a, $h)=(0,0,0,0);
my($dev, $inode, $mode, $nlink, $uid, $gid, $rdev, $size, $time, $mtime, $ctime, $blksize, $blocks);
 
 
foreach (@ARGV){
  if(/^-/){
     if(/l/){ $l =1 ;}
     if(/F/){ $F =1 ;}
     if(/a/){ $a =1 ;}
     if(/h/){ $h =1 ;}
  }     
  else {
     push(@arg, $_);
  }
}
 
if(scalar(@arg)==0){
     push(@arg, '.');
}
 
foreach (@arg){
   my $argment = $_;
   if(-e $argment || die "$!\n"){
     if(-d $argment){
        if($argment ne '/'){
           $argment =~ s/\/$//;
        }
        opendir(D, "$argment") || die "$!\n";
        @x = readdir(D);
     }
     else{
        push (@x, $argment) ;
     }
   }
 
   foreach (@x){
     my $file = $_;
     my $fullpathname;
 
     if(-d $argment){
        $fullpathname = $argment.'/'.$file;     # need full path name to get the info unless traversing the current dir.
     }
     else {
        $fullpathname = $file;
     }
 
     ($dev, $inode, $mode, $nlink, $uid, $gid, $rdev, $size, $time, $mtime, $ctime, $blksize, $blocks) = lstat($fullpathname);
     $type{$file} = (type($fullpathname))[0];           # sub call to get the file type.
     $exec{$file} = (type($fullpathname))[1];           # sub call to get the file type.
     $perm{$file} = perm($mode);                        # sub call to get the permission info.
     $nlink{$file} = $nlink;                            # link count
     $username{$file} = getpwuid($uid);                 # convert uid to user name
     $groupname{$file} = getgrgid($gid);                # convert gid to group name
     $modtime{$file} = strftime("%Y-%m-%d %H:%M", localtime($mtime));   # convert mtime in second to 'Y-M-D H-M' format
     $filesize{$file} = filesize($h, $size);            # sub call to calculate file size
 
     filename($F, $l, $file, $fullpathname);    # sub call to append /, @ or * if needed. 
     fieldlen($nlink{$file}, $username{$file}, $groupname{$file}, $filesize{$file});    # sub call to calculate the field size.
   }
 
   if(-d $argment){
     print "$argment".":\n";
   }
   else {
     print "\n";
   }
 
   disp($l, $F, $a, $h, @x);
 
 
   if(-d $argment){
      closedir(D);
   }
 
   undef(@x);
 
 
}
 
 
 
sub perm {              # subroutine to convert the permission to rwx format.
   my $mode = shift(@_);
   my $p = sprintf("%04o", S_IMODE($mode)); 
   my (@tmp, $perm, $t);
 
   @tmp = split(//, $p);
 
   for(0..2) {
      $t = pop(@tmp);
      SWITCH: {
        ($t == 0) && do {unshift(@tmp, '---') ; last SWITCH; };
        ($t == 1) && do {unshift(@tmp, '--x') ; last SWITCH; };
        ($t == 2) && do {unshift(@tmp, '-w-') ; last SWITCH; };
        ($t == 3) && do {unshift(@tmp, '-wx') ; last SWITCH; };
        ($t == 4) && do {unshift(@tmp, 'r--') ; last SWITCH; };
        ($t == 5) && do {unshift(@tmp, 'r-x') ; last SWITCH; };
        ($t == 6) && do {unshift(@tmp, 'rw-') ; last SWITCH; };
        ($t == 7) && do {unshift(@tmp, 'rwx') ; last SWITCH; };
      }
   }
 
   $t = pop(@tmp);
 
   if($t==1 || $t==3 || $t==5 || $t==7){                # sticky 
        (substr($tmp[2],2,1) eq 'x') ? substr($tmp[2],2,1, 't') : substr($tmp[2],2,1, 'T');
   }
   elsif($t==2 || $t==3 || $t==6 || $t==7){             # sgid
        (substr($tmp[1],2,1) eq 'x') ? substr($tmp[1],2,1, 's') : substr($tmp[1],2,1, 'S');
   }
   elsif($t== 4 || $t==5 || $t==6 || $t==7){            # suid
        (substr($tmp[0],2,1) eq 'x') ? substr($tmp[0],2,1, 's') : substr($tmp[0],2,1, 'S');
   }
 
   $perm = join('', @tmp);
 
   return $perm ; 
}
 
 
sub type {              # subroutine to find the file type
  my $file = shift(@_);
  my $exec = 0;
  my $type;
 
  (-l $file) && do {$type = 'l'} ||     # symbolic link
  (-b $file) && do {$type = 'b'} ||     # block device
  (-c $file) && do {$type = 'c'} ||     # character device
  (-p $file) && do {$type = 'p'} ||     # pipe
  (-S $file) && do {$type = 's'} ||     # socket
  (-d $file) && do {$type = 'd'} ||     # directory
  do {$type = '-'};                     # others
 
  (-x $file) && !(-d $file) && do {$exec = 1} ;
 
  return ($type, $exec);
}
 
 
sub filesize {          # subroutine to convert the file size to in K/M/G.
  my ($h, $size) = @_;
  my $filesize = $size;
  my $len=length($filesize);
 
  if($h && $l){
    if($len > 9){     
        $filesize = substr($size/1000000000, 0, 3);
        $filesize =~ s/\.$//;
        $filesize = $filesize.'G';
    } 
    elsif($len > 6){     
        $filesize = substr($size/1000000, 0, 3);
        $filesize =~ s/\.$//;
        $filesize = $filesize.'M';
    } 
    elsif($len > 3){     
        $filesize = substr($size/1000, 0, 3);
        $filesize =~ s/\.$//;
        $filesize = $filesize.'K';
    } 
  }
 
  return $filesize;
}
 
 
sub filename {          # subroutine to append /, @ or * if needed.
  my ($F, $l, $file, $fullpathname) = @_;
  my ($tgt);
 
  $filename{$file} = $file;
 
  if($F){
    if (-l $fullpathname){
      $filename{$file} = $file.'@';
    }
    elsif(-d $fullpathname){
      $filename{$file} = $file.'/';
    }
    elsif (-f $fullpathname && $exec{$file}){
      $filename{$file} = $file.'*';
    }
  }    
 
  if($l && -l $fullpathname){
      $filename{$file} = "$file".' -> '.readlink($fullpathname) ;
  }
 
  return $filename{$file};
}
 
 
 
sub fieldlen {                  # subroutine to find the longest field for each items to determie the field size upon the printing.
  my ($nlink, $uid, $gid, $size) = @_;
  my($len);
 
  $len = length($nlink);
  ($len > $max_nlink) && do {$max_nlink = $len};
 
  $len = length($uid);
  ($len > $max_uid) && do {$max_uid = $len};
 
  $len = length($gid);
  ($len > $max_gid) && do {$max_gid = $len};
 
  $len = length($size);
  ($len > $max_size) && do {$max_size = $len};
}
 
sub disp {                      # subroutine to display the result.
   my ($l, $F, $a, $h, @x) = @_;
   my $flag = $l.$F.$a.$h ;
 
   SWITCH: {
     ($flag eq '0000') && do { shrt_prn(@x)     ; last SWITCH; };
     ($flag eq '0001') && do { shrt_prn(@x)     ; last SWITCH; };
     ($flag eq '0010') && do { shrt_all_prn(@x) ; last SWITCH; };
     ($flag eq '0011') && do { shrt_all_prn(@x) ; last SWITCH; };
     ($flag eq '0100') && do { shrt_prn(@x)     ; last SWITCH; };
     ($flag eq '0101') && do { shrt_prn(@x)     ; last SWITCH; };
     ($flag eq '0110') && do { shrt_all_prn(@x) ; last SWITCH; };
     ($flag eq '0111') && do { shrt_prn(@x)     ; last SWITCH; };
     ($flag eq '1000') && do { long_prn(@x)     ; last SWITCH; };
     ($flag eq '1001') && do { long_prn(@x)     ; last SWITCH; };
     ($flag eq '1010') && do { long_all_prn(@x) ; last SWITCH; };
     ($flag eq '1011') && do { long_all_prn(@x) ; last SWITCH; };
     ($flag eq '1100') && do { long_prn(@x)     ; last SWITCH; };
     ($flag eq '1101') && do { long_prn(@x)     ; last SWITCH; };
     ($flag eq '1110') && do { long_all_prn(@x) ; last SWITCH; };
     ($flag eq '1111') && do { long_all_prn(@x) ; last SWITCH; };
 
   }
}
 
 
sub shrt_prn {
  foreach (@_){
     if(!/^\./){                ## other than . and ..
        print "$filename{$_}\n";
     }
  }
}
 
sub shrt_all_prn {
  foreach (@_){                 ## all printed out
      print "$filename{$_}\n";
  }
}
 
sub long_prn {
  foreach (@_){
     if(!/^\./){                ## other than . and ..
        printf "%10s %${max_nlink}s %${max_uid}s %${max_gid}s %${max_size}s %15s %-s\n", $type{$_}.$perm{$_},  $nlink{$_}, $username{$_},  $groupname{$_},  $filesize{$_},  $modtime{$_},  $filename{$_};
     }
  }
}
 
sub long_all_prn {
  foreach (@_){
     printf "%10s %${max_nlink}s %${max_uid}s %${max_gid}s %${max_size}s %15s %-s\n", $type{$_}.$perm{$_},  $nlink{$_}, $username{$_},  $groupname{$_},  $filesize{$_},  $modtime{$_},  $filename{$_};
  }
}
 
 
 
 
 

```

---

### Post by slavik on 2010-04-20
I think this one should be restricted to C.

the python submission uses listdir ... no readdir?
the perl submission uses ENV and chdir ... chdir is not a system call.

I believe the intent is to use system calls only, as in, you are writing ls and there is no shell. :)

---

### Post by the_unforgiven on 2010-04-20
> **falconindy said:**
> 
Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.


Sorry, I haven't been following these challenges for a while - been busy with work :(
o. What is the criteria for defining 'beginner' in these challenges?
o. I agree with slavik - at least this one should be restricted to C.

I was wondering if I should submit the code too - hence the 1st question.
It's been a while I've written 'ls' and a shell ;)

---

### Post by slavik on 2010-04-20
found some old code I have written.

This does ls on /

```


#include <stdio.h>
#include <dirent.h>
#include <sys/types.h>

int main() {
        DIR *dptr;
        struct dirent *dstruct;

        dptr = opendir("");
        if (!dptr) { printf("problem\n"); return 1; }
        printf("dptr is not NULL\n");
        while ((dstruct = readdir(dptr)) != NULL) 
                printf("%s\n",dstruct->d_name);
        closedir(dptr);
        return 0;
}

```

---

### Post by pokebirdd on 2010-04-20
Here's what I've got so far:

```
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <dirent.h>
#include <sys/types.h>
#define FLAG_NUM 4

int main(int argc, char *argv[]){
    int ii;
    char path[PATH_MAX];
    DIR *dir;
    struct dirent *dir_entry;
    FILE *fp;
    int flags[FLAG_NUM] = {0};
    enum flag_types{l = 0, a, F, h};

    /* process command line flags */
    for (ii = 0; ii < argc; ii++){
        if (!strcmp(argv[ii], "-l"))
            flags[l] = 1;
        if (!strcmp(argv[ii], "-a"))
            flags[a] = 1;
    }

    getcwd(path, PATH_MAX);
    if (path != NULL)
        printf("%s\n", path);
    else{
        printf("Could not access specified directory\n");
        return 1;
    }

    dir = opendir(path);
    while ((dir_entry = readdir(dir)) != NULL){
        if (dir_entry->d_name[0] != '.' || flags[a]){

            if (flags[l]){
                if ((fp = fopen(dir_entry->d_name, "r")) == NULL){
                    printf("Could not open %s", dir_entry->d_name);
                    return 1;
                }
                fseek(fp, 0, SEEK_END);
                /* print the file size*/
                printf("%ld ", ftell(fp));
                fclose(fp);
            }

            printf("%s\n", dir_entry->d_name);
        }
    }

    return 0;
}
```

The '-l' option only prints the size of the file right now because I can't figure out how to find the permission bits, user id's, etc.

---

### Post by WillFerrellLuva on 2010-04-20
> the python submission uses listdir ... no readdir?

I tried not to use anything that would disqualify me.  Is listdir not allowed?

---

### Post by texaswriter on 2010-04-20
I'm not sure I get why people are insisting on C. C probably would be faster, but i would have to imagine any serious language has to have directory capabilities. 

Anyways, I'll be posting a version in C within a week. Just finishing all the research... lots of research.

---

### Post by the_unforgiven on 2010-04-20
> **texaswriter said:**
> I'm not sure I get why people are insisting on C. C probably would be faster, but i would have to imagine any serious language has to have directory capabilities.
IIUC, it's not about speed at all - it won't be much of a challenge in other languages since most of them simplify life a lot.

---

### Post by texaswriter on 2010-04-20
> **the_unforgiven said:**
> IIUC, it's not about speed at all - it won't be much of a challenge in other languages since most of them simplify life a lot.

Actually, if you read the program request, readdir or listdir is the least of the concerns... Anyways, I'm almost done with all my research... I think I have all the C libraries that I need to complete the requirements, so I'll begin piecing everything together.

---

### Post by johnl on 2010-04-20
> **pokebirdd said:**
> 

The '-l' option only prints the size of the file right now because I can't figure out how to find the permission bits, user id's, etc.

Nice work so far -- take a look at "man 2 stat" for determining all the information you need about the file (including file size).

---

### Post by slavik on 2010-04-20
> **WillFerrellLuva said:**
> I tried not to use anything that would disqualify me.  Is listdir not allowed?
is listdir a syscall?

---

### Post by Tony Flury on 2010-04-21
Slavik, it almost certainly just encapsulates a call to openpath and readdir - and puts the names for the directory entries into a single Python list. Anyone writing this challenge in python would still need to use python equivalents to stat etc to get all the other details.

listdir is not a call to "ls -"

---

### Post by pokebirdd on 2010-04-21
Here's my submission:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <dirent.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <pwd.h>
#include <time.h>
#define FLAG_NUM 4
#define FILE_NAME_MAX 200
#define PATH_NUM_MAX 100

enum flag_types{l = 0, a, F, h};

int len_dir(DIR *dir, int all);
char *human_size(long int size);
void list_dir(char *path, int flags[]);

int main(int argc, char *argv[]){
    int ii;
    int flags[FLAG_NUM] = {0};
    char path[PATH_NUM_MAX][PATH_MAX];
    int path_num = 0;

    /* process command line flags */
    for (ii = 1; ii < argc; ii++){
        if (!strcmp(argv[ii], "-l"))
            flags[l] = 1;
        else if (!strcmp(argv[ii], "-a"))
            flags[a] = 1;
        else if (!strcmp(argv[ii], "-F"))
            flags[F] = 1;
        else if (!strcmp(argv[ii], "-h"))
            flags[h] = 1;
        else
            strncpy(path[path_num++], argv[ii], PATH_MAX);
    }

    if (path_num){
        for (ii = 0; ii < path_num; ii++){
            printf("%s:\n", path[ii]);
            list_dir(path[ii], flags);
        }
    }
    else{
        getcwd(path[0], PATH_MAX);
        if (path[0] == NULL){
            printf("Cannot access %s\n", path[0]);
            return 1;
        }

        list_dir(path[0], flags);
    }

    return 0;
}

int len_dir(DIR *dir, int all){
    struct dirent *dir_entry;
    int len = 0;
    while ((dir_entry = readdir(dir)) != NULL){
        if (dir_entry->d_name[0] != '.' || all)
            len++;
    }
    /* reset the position of the dir stream */
    seekdir(dir, 0);
    return len;
}

char *human_size(long int size){
    char *tmp = malloc(20); //20 chars is enough i think?
    if (size/1000 == 0)
        snprintf(tmp, 20, "%ld", size);
    else if (size/1000 < 10)
        snprintf(tmp, 20, "%.1fK", size/1000.0);
    else if (size/1000 < 1000)
        snprintf(tmp, 20, "%3.0fK", size/1000.0);
    else if (size/1000000 < 10)
        snprintf(tmp, 20, "%.1fM", size/1000000.0);
    else if (size/1000000 < 1000)
        snprintf(tmp, 20, "%3.0fM", size/1000000.0);
    else if (size/1000000000 < 10)
        snprintf(tmp, 20, "%.1fG", size/1000000000.0);
    else if (size/1000000000 < 1000)
        snprintf(tmp, 20, "%3.0fG", size/1000000000.0);

    return tmp;
}

void list_dir(char *path, int flags[]){
    int ii;
    char tmp[20];
    DIR *dir;

    struct dirent *dir_entry;
    struct tm *time;
    int dir_len;
    int max_usr_len = 0;
    int max_grp_len = 0;
    int max_size_len = 0;

    struct stat **stat_infos;
    char **dir_names;
    int sp = 0; /*pointer for dir_names and stat_names*/

    dir = opendir(path);
    if (dir == NULL){
        printf("Cannot access %s\n", path);
        return;
    }
    dir_len = len_dir(dir, flags[a]);
    stat_infos = malloc(dir_len * sizeof(struct stat *));
    dir_names = malloc(dir_len * sizeof(char *));

    /* read the directory */
    while ((dir_entry = readdir(dir)) != NULL){
        if (dir_entry->d_name[0] != '.' || flags[a]){
            stat_infos[sp] = malloc(sizeof(struct stat));
            dir_names[sp] = malloc(FILE_NAME_MAX);
            stat(dir_entry->d_name, stat_infos[sp]);
            strncpy(dir_names[sp], dir_entry->d_name, FILE_NAME_MAX);

            if (strlen(getpwuid(stat_infos[sp]->st_uid)->pw_name) > max_usr_len)
                max_usr_len = strlen(getpwuid(stat_infos[sp]->st_uid)->pw_name);
            if (strlen(getpwuid(stat_infos[sp]->st_gid)->pw_name) > max_grp_len)
                max_grp_len = strlen(getpwuid(stat_infos[sp]->st_gid)->pw_name);
            snprintf(tmp, 20, "%ld", stat_infos[sp]->st_size);
            if (strlen(tmp) > max_size_len)
                max_size_len = strlen(tmp);
                
            sp++;
        }
    }

    /* print the directory info */
    for (ii = 0; ii < dir_len; ii++){
        if (flags[l]){
            /* permission bits */
            printf("%03o ", stat_infos[ii]->st_mode&0777);
            /* user name */
            printf("%*s ", max_usr_len, getpwuid(stat_infos[ii]->st_uid)->pw_name);
            /* group name */
            printf("%*s ", max_grp_len, getpwuid(stat_infos[ii]->st_gid)->pw_name);
            /* file size */
            if (flags[h])
                printf("%s ", human_size(stat_infos[ii]->st_size));
            else
                printf("%*ld ", max_size_len, stat_infos[ii]->st_size);
            /* modification time */
            time = localtime(&(stat_infos[ii]->st_mtime));
            printf("%4d-%02d-%02d %02d:%02d ", time->tm_year+1900, time->tm_mon+1, time->tm_mday, time->tm_hour, time->tm_min);
        }
        printf("%s", dir_names[ii]);

        if (flags[F]){
            if ((stat_infos[ii]->st_mode & ~0777) == S_IFDIR)
                printf("/");
            else if (stat_infos[ii]->st_mode & S_IXUSR)
                printf("*");
        }

        if (flags[l])
            printf("\n");
        else
            printf(" ");
    }

    if (!flags[l])
        printf("\n");
}    
```

There are a few things I couldn't find the documentation for. Can someone give me a link or tell me what each of the symbols for the -F option stand for?

---

### Post by the_unforgiven on 2010-04-21
> **pokebirdd said:**
> There are a few things I couldn't find the documentation for. Can someone give me a link or tell me what each of the symbols for the -F option stand for?
Check the [coreutils/ls]("http://www.gnu.org/software/coreutils/manual/html_node/General-output-formatting.html#General-output-formatting") info page.

---

### Post by ApEkV2 on 2010-04-21
My submission in C, if there needs to be comments, I'll insert them. Total length: 219 lines.
To run this code, compile with "gcc -O2 <path to source>" and then execute the a.out.
Completed tasks: d flag, h flag, i flag, l flag, R flag, recursion, long options, file path arguments, octal to letter permissions, uid/gid resolving.
Incomplete: a flag, F flag, time of last modification.
```
/*  Created by ApEk  //  Usage: command [path(s)] [option(s)]  _______________*/
/******************************************************************************/
#include <dirent.h>
#include <errno.h>
#include <getopt.h>
#include <grp.h>
#include <pwd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*____________________________________________________________________________*/
/******************************************************************************/

void PrintUsage(void);			// Prints the command usage
void Convert(struct stat);		// Convert permissions to letter
void Toptier(const char*);		// Recursive function to handle directory/file traversal
void HumanReadable(size_t);		// Convert sizes to human format
void Display(const char*, const char*);	// Display entry information

int a_switch, d_switch, f_switch,		// Global switches
    h_switch, i_switch, l_switch, r_switch;

static struct option const long_options[] =
{
	{"all",			0, 0, 'a'},
	{"directory",		0, 0, 'd'},
	{"classify",		0, 0, 'F'},
	{"human-readable",	0, 0, 'h'},
	{"inode",		0, 0, 'i'},
	{"recursive",		0, 0, 'R'},
	{0, 0, 0, 0}
};			// long options ^

/*____________________________________________________________________________*/
/******************************************************************************/

int main(int argc, char *argv[])
{
	struct stat buf;
	int x = 0, c, length = pathconf(".",_PC_PATH_MAX);
	while ((c = getopt_long(argc, argv,"adFhilR", long_options, &x)) != -1)
	{
		switch(c) {
			case 'a': a_switch = 1; // TODO
		break;
			case 'd': d_switch = 1; // Done
		break;
			case 'F': f_switch = 1; // TODO
		break;
			case 'h': h_switch = 1; // Done
		break;
			case 'i': i_switch = 1; // Done
		break;
			case 'l': l_switch = 1; // Done
		break;
			case 'R': r_switch = 1; // Done
		break;
			case '?': PrintUsage(); // HELP
		return 1;
			default: break;
		}
	}

	// Handle individual paths as arguments, if a valid path is found,
	// turn off using cwd by switching c to 0...kinda ugly ?

	for (x = 1, c = 1; argv[x] != NULL; ++x) {
		if (!stat(argv[x],&buf))
		{ 
			if (c) c = 0; // turn off cwd
			if (S_ISDIR(buf.st_mode)) {
				printf("%c[%d;%dm%s%c[%dm\n",27,1,34,argv[x],27,0);
				Display(argv[x], NULL);
				Toptier(argv[x]);
			}
			else if (S_ISREG(buf.st_mode)) {
				printf("%s\n",argv[x]);
				Display(argv[x], NULL);
			}
		}
	}

	// If no valid paths are found, use the cwd

	if (c) {
		char *current = malloc (length);
		Toptier(getcwd(current,length));
		free(current);
	}
	
        return 0;
}

/*____________________________________________________________________________*/
/******************************************************************************/
// This function handles the recursion, if malloc fails, skip that entry.
// If the current entry is a directory and r_switch is enabled, Display first then enter.
// Free the memory pointed to by path before jumping back.

void Toptier(const char *argv)
{
	struct dirent *dep;
	DIR *dirp = opendir(argv);
	if (dirp == NULL) {
		printf("1%9d\n", errno);
		return; // opendir error
	}

	while ((dep = readdir(dirp)) != NULL) {		
		if (!strcmp(".",dep->d_name) || !strcmp("..",dep->d_name))
			continue;  //  skip these entries

		char *path = malloc(strlen(argv) + strlen(dep->d_name)+2);
		if (path) sprintf(path,"%s/%s", argv, dep->d_name);
		else	continue;

		if (dep->d_type == DT_DIR) {
			Display (path, dep->d_name);
			if (r_switch) Toptier(path);
		}
		else if (dep->d_type == DT_REG && !d_switch) {
			Display (path, dep->d_name);
		}
		free(path);
	}
	closedir(dirp);
}

/*____________________________________________________________________________*/
/******************************************************************************/
// This function displays properties for the files and directories.
// First if long format is on, call Convert to change octal permissions to letter.
// If human-readable is on, call HumanReadable to make sizes human-readable.
// If inode is on, print the inode and lastly print the name of the entry.

void Display(const char *path, const char *name)
{
	struct stat buf;
	if (stat(path,&buf) == -1) {
		printf("2%9d\n", errno);
		return; // stat error
	}
	
	if (l_switch) {
		Convert(buf); // convert long format
		
		if (h_switch) HumanReadable(buf.st_size);
		else printf("%10d", (int)buf.st_size);
	}
	
	if (i_switch) printf("%10d", (int)buf.st_ino);
	if (name == NULL) printf("\n");
	else if	(!(S_ISDIR(buf.st_mode))) printf(" %s\n",name);
		else printf(" %c[%d;%dm%s%c[%dm\n",27,1,34,name,27,0);
}

/*____________________________________________________________________________*/
/******************************************************************************/
//  This function changes octal to letter permissions, and
//  Resolves the gid/uid numbers returned by the stat function.

void Convert(struct stat buf)
{
	int x = 0;
	struct group *grp;  // required for getgrgid()
	struct passwd *pwd; // required for getpwuid()
	char permission[10] = "----------";
	
	if (buf.st_mode & S_IFDIR) permission[0] = 'd';
	if (buf.st_mode & S_IRUSR) permission[1] = 'r';
	if (buf.st_mode & S_IWUSR) permission[2] = 'w';
	if (buf.st_mode & S_IXUSR) permission[3] = 'x';
	if (buf.st_mode & S_IRGRP) permission[4] = 'r';
	if (buf.st_mode & S_IWGRP) permission[5] = 'w';
	if (buf.st_mode & S_IXGRP) permission[6] = 'x';
	if (buf.st_mode & S_IROTH) permission[7] = 'r';
	if (buf.st_mode & S_IWOTH) permission[8] = 'w';
	if (buf.st_mode & S_IXOTH) permission[9] = 'x';
	for (; x < 10; ++x) printf("%c",permission[x]);
	
	if ((pwd = getpwuid(buf.st_uid)) && (grp = getgrgid(buf.st_gid))) 
		printf("%2d %-8.8s%-8.8s",buf.st_nlink, pwd->pw_name, grp->gr_name);
	else 
		printf("%2d %d %d",buf.st_nlink, buf.st_uid, buf.st_gid);
}

/*____________________________________________________________________________*/
/******************************************************************************/

void HumanReadable(size_t size)
{
	size_t tmp = size;
	if ((tmp/1000) < 10)
		printf("%9.2g Kb",(double)tmp/1000);
	else if ((tmp/1000) < 1000)
		printf("%9.2g Kb",(double)tmp/1000);
	else if ((tmp/1000000) < 10)
		printf("%9.2g Mb",(double)tmp/1000000);
	else if ((tmp/1000000) < 1000)
		printf("%9.2g Mb",(double)tmp/1000000);
	else if ((tmp/1000000000) < 10)
		printf("%9.2g Gb",(double)tmp/1000000000);
	else if ((tmp/1000000000) < 1000)
		printf("%9.2g Gb",(double)tmp/1000000000);
}

/*____________________________________________________________________________*/
/******************************************************************************/

void PrintUsage(void)
{
	printf("\nUsage: command [paths] [options]\n\n"
		"\t-a  --all\t\tDon't ignore entries starting with .\n"
		"\t-d  --directory\t\tDisplay directories only\n"
		"\t-F  --classify\t\tAppend indicator (one of */=>@|) to entries\n"
		"\t-h  --human-readable\tUse human readable sizes\n"
		"\t-i  --inode\t\tPrint inode\n"
		"\t-l\t\t\tUse a long listing format\n"
		"\t-R  --recursive\t\tList subdirectories recursively\n\n");
}
```
Example output - a.out -l /home/mclovin/dwhelper
```
**[color=blue]/home/mclovin/dwhelper[/color]**
drwxr-xr-x 3 mclovin mclovin       4096
-rw-r--r-- 1 mclovin mclovin    2870841 Swift can fly_____.mp4
-rw-r--r-- 1 mclovin mclovin   39040205 Descent_ Like never seen before.mp4
-rw-r--r-- 1 mclovin mclovin    4749269 Powerthirst 3_ Powermost.mp4
-rw-r--r-- 1 mclovin mclovin    1987309 Super Awesome Brothers.mp4
drwxr-xr-x 2 mclovin mclovin       4096 **[color=blue]Awesome[/color]**
-rw-r--r-- 1 mclovin mclovin    2030379 Contra vs. Duck Hunt.mp4
-rw-r--r-- 1 mclovin mclovin     490277 GTA 4 ICE CREAM SPLAT.mp4
```
ls output: ls -l /home/mclovin/dwhelper
```
total 49988
drwxr-xr-x 2 mclovin mclovin     4096 2010-05-07 10:37 **[color=blue]Awesome[/color]**
-rw-r--r-- 1 mclovin mclovin  2030379 2010-03-25 22:12 **[color=purple]Contra vs. Duck Hunt.mp4[/color]**
-rw-r--r-- 1 mclovin mclovin 39040205 2010-02-09 15:05 **[color=purple]Descent_ Like never seen before.mp4[/color]**
-rw-r--r-- 1 mclovin mclovin   490277 2010-03-25 22:24 **[color=purple]GTA 4 ICE CREAM SPLAT.mp4[/color]**
-rw-r--r-- 1 mclovin mclovin  4749269 2010-05-01 09:22 **[color=purple]Powerthirst 3_ Powermost.mp4[/color]**
-rw-r--r-- 1 mclovin mclovin  1987309 2010-05-03 13:08 **[color=purple]Super Awesome Brothers.mp4[/color]**
-rw-r--r-- 1 mclovin mclovin  2870841 2010-03-25 22:30 **[color=purple]Swift can fly_____.mp4[/color]**
```
Changed:  Some minor cleanup, and reused the single character variables, added PrintUsage, figured out octal to letter, humanreadable function, 
figured out getpwuid, global ints are initialized to zero by default (didn't know that), and tweaked output.

---

### Post by texaswriter on 2010-04-26
Just so people know, I am making my program and hope to have it uploaded today or tomorrow-ish. It'll be in C.

Edit: Eh, well, more research is needed. This is kind of hard, not beginner at all. You need to much documentation that is not easily found... I've found documentation on all the libraries I need, but it has all been insufficient. I am currently researching macros for the stat.h derived functions. I'm also moving this week, so if the competition happens to end.... 
OH yeah, the sorting to display it like ls does would be pretty hard too unless there are macros for that too.

---

### Post by ApEkV2 on 2010-05-08
BUMP, there needs to be more code in this thread right now!
btw for anyone using C, if you need to learn about a certain function google "*function name* opengroup"

---

### Post by GregBrannon on 2010-05-22
Bump!

Is there an end to this challenge?

---

### Post by texaswriter on 2010-05-22
Heh, lol, having finished finals and all, guess I'll try to finish mine up quick... But if somebody wants to end the challenge, don't wait on me... 

I have had to learn too many things to get the code submitted in a timely manner. 

Once you figure out the macro's, it's not too hard.

---

### Post by lonewaster on 2010-05-22
so are there no imposed limitations on choice of language?

also, how **usable** must the end result be?
for instance, if i made it in perl you would need to run
```
perl easy-ls.pl --flags
```and similar with php.

Could i compile it all into 2 files-
 +   a perl file to do the main work
 +   a bash script to make it runnable from terminal without the use of '*** perl script.pl --flags*** '

and then the end user would copy those two files into /usr/bin or any other PATH directory (i have a /home/billy/bin directory on my lappy for any scripts i do for myself.).//
that way, it could be run as a command, such as '*** easy-ls --flags ***' instead.

just a...hypothetical...question :D

---

### Post by Bachstelze on 2010-05-22
> **lonewaster said:**
> 
 +   a bash script to make it runnable from terminal without the use of '*** perl script.pl --flags*** '

and then the end user would copy those two files into /usr/bin or any other PATH directory (i have a /home/billy/bin directory on my lappy for any scripts i do for myself.).//
that way, it could be run as a command, such as '*** easy-ls --flags ***' instead.

That's what the "shebang" line is for.

---

### Post by texaswriter on 2010-05-22
Yeah, no imposed restrictions. I just don't think there is the "hard" way to do it in many languages. In C, obviously you can do things as close to assembly almost as is possible in a HLL, so there is always a hard way to do anything. 

I don't know these other languages so well, so I am just conjecturing. Needless to say, I have to say there must be an easier way to do this. Most applications in Linux that run in a GUI environment have a gtk_ or g_  something that will create a window for browsing directories, if I am not mistaken. I haven't used it, but saw something to that effect when messing around in Anjuta. 

In a terminal app: system("ls") would be highly effective. 
> **lonewaster said:**
> so are there no imposed limitations on choice of language?

also, how **usable** must the end result be?
for instance, if i made it in perl you would need to run
```
perl easy-ls.pl --flags
```and similar with php.

Could i compile it all into 2 files-
 +   a perl file to do the main work
 +   a bash script to make it runnable from terminal without the use of '*** perl script.pl --flags*** '

and then the end user would copy those two files into /usr/bin or any other PATH directory (i have a /home/billy/bin directory on my lappy for any scripts i do for myself.).//
that way, it could be run as a command, such as '*** easy-ls --flags ***' instead.

just a...hypothetical...question :D

---

### Post by texaswriter on 2010-05-22
EDIT: UPLOADED UPDATED CODE. Please see a later post for this. Thanks

OK, after many promises and much research, here is my first version. 

It doesn't support everything it's supposed to, but it functions properly for "ls -a" or "ls / /home /directories". 

Recursion, -h, -R -l -F are still underway. 

Any comments and suggestions are welcome. 

Mostly what I am waiting on for -F is what the symbols mean and how to detect them.  As in: */=>@|

Thanks

The code is attached. 

It can be compiled like: gcc -x c filename.txt -o filename

It should mostly pass any -Wall compilation too, though I haven't completely gone through the warnings.

---

### Post by lonewaster on 2010-05-22
> **texaswriter said:**
> Yeah, no imposed restrictions. I just don't think there is the "hard" way to do it in many languages. In C, obviously you can do things as close to assembly almost as is possible in a HLL, so there is always a hard way to do anything. 

I don't know these other languages so well, so I am just conjecturing. Needless to say, I have to say there must be an easier way to do this. Most applications in Linux that run in a GUI environment have a gtk_ or g_  something that will create a window for browsing directories, if I am not mistaken. I haven't used it, but saw something to that effect when messing around in Anjuta. 

In a terminal app: system("ls") would be highly effective.

see..uhm..i thought that the idea was to make sort of 'your own' ***ls*** system/application/command ??
if so..then wouldn't using system('ls'); be...cheating??

:guitar:

---

### Post by ApEkV2 on 2010-05-22
> if so..then wouldn't using system('ls'); be...cheating??
technically not cheating, but against the rules of the challenge nonetheless.
...the rules are located in...the first post.
Is it me, but did the op kinda disappear off the face of the earth?

@ texas, your getting a pm asap...some things must be mentioned
Also you should include your code in the actual post and not as an attachment. 
Non-members will not be able to see it, and it becomes a hassle for members.

---

### Post by texaswriter on 2010-05-23
Thanks ApEkV2 for the helpful comments on my code. I have tried to correct as many things as possible. If somebody can answer my question on my previous post, the one with the previous code, I'll finish this program. Otherwise, I've learned enough, that I could call it a rest. 
EDIT: UDPATED CODE, PLEASE SEE LATEST POST BY ME WITH CODE !!!
see later post for latest code

---

### Post by texaswriter on 2010-05-23
> **ApEkV2 said:**
> technically not cheating, but against the rules of the challenge nonetheless.
...the rules are located in...the first post.
Is it me, but did the op kinda disappear off the face of the earth?

  

Yeah, somebody is going to have to PM the OP or possibly step in and judge the finalists them self. 

Anyways, to answer the previous question, system("ls") IS cheating for this competition. I hope I didn't accidentally say it was ok, I was speaking if somebody was ACTUALLY trying to get a directory read in a CLI program. Obviously, some pre-written utility would be preferable to writing all this code.

---

### Post by AdotB on 2010-05-25
I don't know if this is still open or not, but I thought I'd give it a shot.

I tried to match the behavior of ls as much as possible for the options I implemented.

I hope its not too obfuscated. I'm not too good at the scale and organizing of the big picture yet.

```
#!/usr/bin/env ruby
require 'optparse'

##
# Default color values, matching gnu ls
LsColors = {
    'lc' => "\033[",    # lc: left of color sequence
    'rc' => "m",        # rc: right of color sequence
    'ec' => nil,        # ec: end color (replaces lc+no+rc)
    'rs' => "0",        # rs: reset to ordinary colors
    'no' => "0",        # no: normal
    'fi' => nil,        # fi: file: default
    'di' => "01;34",    # di: Directory: bright blue
    'ln' => "01;36",    # ln: Symlink: bright cyan
    'pi' => "33",       # pi: Pipe: yellow/brown
    'so' => "01;35",    # so: Socket: bright magenta
    'bd' => "01;33",    # bd: Block device: bright yellow
    'cd' => "01;33",    # cd: Char device: bright yellow
    'mi' => "0",        # mi: Missing file: undefined
    'or' => "0",        # or: Orphaned symlink: undefined 
    'ex' => "01;32",    # ex: Executable: bright green
    'do' => "01;35",    # do: Door: bright magenta
    'su' => "37;41",    # su: setuid: white on red
    'sg' => "30;43",    # sg: setgid: black on yellow
    'st' => "37;44",    # st: sticky: black on blue
    'ow' => "34;42",    # ow: other-writable: blue on green
    'tw' => "30;42",    # tw: ow w/ sticky: black on green
    'ca' => "30;41",    # ca: black on red
    'mh' => nil,        # mh: disabled by default
    'cl' => "\033[K",   # cl: clear to end of line
}

Permissions = ['---', '--x', '-w-', '-wx', 'r--', 'r-x', 'rw-', 'rwx']

##
# indicators for -F classify
Indicators = {
    'exec'      => '*',
    'directory' => '/',
    'link'      => '@',
    'socket'    => '=',
    'fifo'      => '|',
    'door'      => '>'
}

##
# Get color settings from environmental variable.
#
def parse_colors
    env_colors = ENV['LS_COLORS']
    if env_colors
        env_colors.split(':').each do |pair|
            key, val = pair.split('=')
            LsColors[key] = val
        end
    end

    #
    # ec: end color (replaces lc+no+rc)
    LsColors['ec'] = LsColors['lc'] + LsColors['no'] + LsColors['rc']
end

##
# Format the file size in long output according to options.
#
def fmt_size( size )
    ##
    # In human-readable mode, file sizes will only show a decimal point
    # when less then 10, fitting a 4-character wide field (e.g. 1.2M)
    # This seems to match the behavior of GNU ls.
    #
    kilo = $options[:kilo]  # normally 1024, use 1000 with --si option
    if $options[:human_readable]
        size = if size > 1024**3
            size /= kilo**3.0
            if size >= 10
                "%iG" % size.ceil
            else
                "%0.1fG" % size
            end
        elsif size > kilo**2
            size /= kilo**2.0
            if size >= 10
                "%iM" % size.ceil
            else
                "%0.1fM" % size
            end
        elsif size > kilo
            size /= kilo.to_f
            if size >= 10
                "%iK" % size.ceil
            else
                "%0.1fK" % size
            end
        else
            size.to_s
        end
    else
        size = size.to_s
    end
    return size
end

##
# Format the filename according to options
#
def fmt_name( path, ftype=File.ftype(path), stats=nil )
    
    name = File.basename(path)

    ##
    # Print filenames in certain colors if --color option is selected.
    #
    if $options[:color]
        #
        # To prevent errors, check if the file 
        if File.exist?( path )
            #
            # apply colors according to 
            color = if ftype == 'link'
                LsColors['ln']
            elsif ftype == 'directory'
                LsColors['di']
            elsif ftype == 'fifo'
                LsColors['pi']
            elsif ftype == 'socket'
                LsColors['so']
            elsif ftype == 'characterSpecial'
                LsColors['cd']
            elsif ftype == 'blockSpecial'
                LsColors['bd']
            elsif File.setuid?( path )
                LsColors['su']
            elsif File.setgid?( path )
                LsColors['sg']
            elsif File.sticky?( path ) && File.world_writable?( path )
                LsColors['tw']
            elsif File.sticky?( path )
                LsColors['st']
            elsif File.stat(path).nlink > 1
                LsColors['hl']
            elsif File.executable?( path )
                LsColors['ex']
            #
            # File.world_writable doesnt see to be in ruby 1.8, so check
            # ruby version for this.
            elsif RUBY_VERSION.to_f >= 1.9 && File.world_writable?( path )
                LsColors['ow']
            #
            # If the file does not match the above criteria, but its extention
            # is included in the LS_COLORS environmental variable, apply color
            elsif LsColors.include?( '*' + File.extname(path) )
                LsColors[ '*' + File.extname(path) ]
            #
            # Default to fi (file). Normally the terminals normal color,
            # but can be changed by setting it in the LS_COLORS env variable
            else
                LsColors['fi']
            end
        #
        # If the file (or a link's target) does not exist, set as orphaned.
        else
            color = LsColors['or']
        end
        
        #
        # wrap the file name with the color codes
        if color
            name = LsColors['lc'] + color + LsColors['rc'] + name + LsColors['ec']
        end
    end

    ##
    # When in `long' mode, the name of a link also contains the target.
    # The target classify and color formatting will reflect the end target,
    # even when the direct target is another link.
    #
    if $options[:long] && ftype == 'link'
        target = File.readlink(path)
        begin
            target_type = File.ftype(target)
            while target_type == 'link' do
                target_target ||= File.readlink(target_target)
                target_type = File.ftype(target_target)
            end
        rescue
            target_type = 'missing'
        end
        name += ' -> ' + fmt_name(target, target_type)
    #
    # append classify indicators
    elsif $options[:classify]
        if ftype == 'link'
            name += Indicators[ftype]
        elsif ftype == 'directory'
            name += Indicators[ftype]
        elsif Indicators.include?( ftype )
            name += Indicators[ftype]
        elsif File.executable?(path)
            name += Indicators['exec']
        end
    end

    return name
end

##
# Long listing method, showing detailed information about each file/dir
def long_list( listing )
    field_lengths = [ 1, 9, 1, 1, 1, 1, 1, 1 ] # length of each field in long output
    split_listings = []
    total = 0
    listing.each do |file|
        ftype = File.ftype(file)
        parts = case ftype
        when 'link'
            ['l']
        when 'directory'
            ['d']
        when 'characterSpecial'
            ['c']
        when 'blockSpecial'
            ['b']
        when 'fifo'
            ['p']
        when 'socket'
            ['s']
        when 'file'
            ['-']
        when 'unknown'  # not sure what to put if it's unknown, prob `-'
            ['?']
        else            # assume anything else is unknown
            ['?']
        end
        if ftype == 'link'
            stats = File.lstat(file)
        else
            stats = File.stat(file)
        end
        parts.push(("%o" % stats.mode)[-3,3].chars.map{|c|
                Permissions[c.to_i]}.join)
        parts.push(stats.nlink.to_s)
        if $options[:long] == 'numeric'
            parts.push(stats.uid.to_s)
            parts.push(stats.gid.to_s)
        else
            parts.push( Etc::getpwuid(stats.uid).name )
            parts.push( Etc::getgrgid(stats.gid).name )
        end
        parts.push(fmt_size(stats.size))
        parts.push(stats.mtime.strftime("%Y-%m-%d %H:%M"))
        total += stats.size
        parts.push( fmt_name(file, ftype) )

        ##
        # Determine field lengths for long output by setting them to the longest
        # entry in that field.
        parts.length.times do |i|
            field_lengths[i] = parts[i].length if field_lengths[i] < parts[i].length
        end

        split_listings.push( parts )
    end
    
    output = ""
    ##
    # If listing is a directory, print the total size
    #
    if listing.length > 1
        if $options[:human_readable]
            output += "total #{fmt_size(total)}\n"
        else
            output += "total #{total / 1024}\n"
        end
    end
    
    ##
    # format each line
    field_lengths[-1] = -1  # left-justify last field
    unless $options[:long] == 'numeric'
        field_lengths[3] *= -1  # left-justify owner field
        field_lengths[4] *= -1  # left-justify group field
    end
    line_fmt = "%#{field_lengths[0]}s%#{field_lengths[1..-1].join('s %')}s\n"
    split_listings.each{ |parts| output += ( line_fmt % parts ) }

    return output
end

##
# normal listing. Show only file names
def short_list( listing )
    output = ""
    if $options[:one]
        listing.each{ |path| output += fmt_name(path) + "\n" }
    else
        #
        # ! Fix this to match normal multi-column output.
        # This is temporary until multi-columns is implemented.
        $options[:one] = true
        output = short_list( listing )
    end

    return output
end

##
# Determine whech files and directories to list, then list use appropriate
# method to list them according to the options.
def get_listing( paths=$options[:paths] )
    paths.sort!
    files = [] # will hold non-directories
    dirs  = [] # will hold directories to be listed after files
    paths.each do |path|
        unless File.exist?( path )
            begin
                File.lstat( path )
            rescue
                STDERR.write "#{File.basename(__FILE__)}: cannot access #{path
                        }: No such file or directory\n"
                paths -= [path]
                next
            end
        end
        ##
        # if -d option is not used, list contents of directories
        if File.directory?( path ) && ! $options[:directory]
            listing = Dir.entries( path )
            unless $options[:all]
                listing = listing.map{|p| p unless /^\./ =~ p}.compact
            end
            dirs.push( listing.map{ |p| File.join(path, p) }.sort )
        else
            files.push( path )
        end
    end

    ##
    # Get listings for files then each directory.
    # For some reason, an empty array sometimes gets pushed into dirs, we
    # remove that here as well.
    ([files] + dirs - [[]]).each do |files|
        #
        # print directory name unless its the top or only directory
        #
        unless files.empty? || paths.include?( files[0] ) || dirs.length == 1
            puts "\n" + File.dirname( files[0] ) +":\n" 
        end

        ##
        # Get listing for files
        if $options[:long]
            puts long_list( files )
        else
            puts short_list( files )
        end
    end
end

##
# Get options from command line arguments
#
$options = {
    :kilo=> 1024    # power of bytes for human readable mode. change with --si
}

OptionParser.new do |opts|
    opts.banner = "Usage: #{__FILE__} [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).\n"
    opts.summary_width  = 29
    opts.summary_indent = "  "
    newl = "\n" + " " * opts.summary_width + opts.summary_indent

    opts.on("-l", "use a long listing format") do
        $options[:long] = true
        require 'etc'
    end
    opts.on("-a", "--all", "do not ignore entries starting with .") do
        $options[:all] = true
    end
    opts.on("--color=[WHEN]",
            "control whether color is used to distinguish file#{
            newl}types.  WHEN may be `never', `always', or `auto'") do |colors|
        ##
        # default to `auto'
        colors = 'auto' unless colors

        case colors
        when 'always', 'yes', 'force'
            $options[:color] = true
        when 'never', 'no', 'none'
            $options[:color] = false
        when 'auto', 'tty', 'if-tty'
            $options[:color] = true if STDIN.tty?
        else
            STDERR.write "#{File.basename($0)}: invalid argument `#{colors}' for `--color'
Valid arguments are:
  - `always', `yes', `force'
  - `never', `no', `none'
  - `auto', `tty', `if-tty'
Try `ls --help' for more information.\n"
            exit(1)
        end

        ##
        # parse environmental variable: LS_COLORS
        parse_colors if $options[:color]
    end
    opts.on("-d", "--directory", "list directory entries instead of contents,#{
            newl}and do not dereference symbolic links") do
        $options[:directory] = true
    end
    opts.on("-F", "--classify", "append indicator (one of */=>@|) to entries") do
        $options[:classify] = true
    end
    opts.on("-h", "--human-readable",
            "with -l, print sizes in human readable format#{newl}(e.g., 1K 234M 2G)") do
        $options[:human_readable] = true
    end
    opts.on("--si", "likewise, but use powers of 1000 not 1024") do
        $options[:kilo] = 1000
    end
    opts.on("-n", "--numiric-uid-gid", "like -l, but list numeric user and group IDs") do
        $options[:long] = "numeric"
    end

    opts.on("-1", "list one file per line") do
        $options[:one] = true
    end
    
    opts.on("--help", "display this help and exit") do
        puts opts.banner + "\n"
        puts opts.summarize( [], 26 )
        exit
    end
end.parse!

##
# Get paths to list from remaining arguments
#
$options[:paths] = []
ARGV.sort.each{ |arg| $options[:paths].push(arg) }
$options[:paths].push('.') if $options[:paths].empty?

##
# Get the listing
#
get_listing($options[:paths])
```

Anyway, whether or not this challenge is still open, any pointers would be appreciated.

---

### Post by Bodsda on 2010-05-28
If this challenge is not judged by 12:00 31/05/2010 UTC, the Beginners Team will take over the judging.

Thanks to everyone who has contributed so far. Keep up the good work! 

Happy Coding,
Bodsda

---

### Post by texaswriter on 2010-05-30
see later post for latest code

---

### Post by AdotB on 2010-05-30
I've updated my code a little.

I fixed the ugly invalid option crash,
and also added multi-column short view similar to(but not exactly) the normal ls command.

```
#!/usr/bin/env ruby
require 'optparse'
ProgramName = File.basename(__FILE__)

##
# Default color values, matching gnu ls
LsColors = {
    'lc' => "\033[",    # lc: left of color sequence
    'rc' => "m",        # rc: right of color sequence
    'ec' => nil,        # ec: end color (replaces lc+no+rc)
    'rs' => "0",        # rs: reset to ordinary colors
    'no' => "0",        # no: normal
    'fi' => nil,        # fi: file: default
    'di' => "01;34",    # di: Directory: bright blue
    'ln' => "01;36",    # ln: Symlink: bright cyan
    'pi' => "33",       # pi: Pipe: yellow/brown
    'so' => "01;35",    # so: Socket: bright magenta
    'bd' => "01;33",    # bd: Block device: bright yellow
    'cd' => "01;33",    # cd: Char device: bright yellow
    'mi' => "0",        # mi: Missing file: undefined
    'or' => "0",        # or: Orphaned symlink: undefined 
    'ex' => "01;32",    # ex: Executable: bright green
    'do' => "01;35",    # do: Door: bright magenta
    'su' => "37;41",    # su: setuid: white on red
    'sg' => "30;43",    # sg: setgid: black on yellow
    'st' => "37;44",    # st: sticky: black on blue
    'ow' => "34;42",    # ow: other-writable: blue on green
    'tw' => "30;42",    # tw: ow w/ sticky: black on green
    'ca' => "30;41",    # ca: black on red
    'mh' => nil,        # mh: disabled by default
    'cl' => "\033[K",   # cl: clear to end of line
}

Permissions = ['---', '--x', '-w-', '-wx', 'r--', 'r-x', 'rw-', 'rwx']

##
# indicators for -F classify
Indicators = {
    'exec'      => '*',
    'directory' => '/',
    'link'      => '@',
    'socket'    => '=',
    'fifo'      => '|',
    'door'      => '>'
}

##
# Get color settings from environmental variable.
#
def parse_colors
    env_colors = ENV['LS_COLORS']
    if env_colors
        env_colors.split(':').each do |pair|
            key, val = pair.split('=')
            LsColors[key] = val
        end
    end

    #
    # ec: end color (replaces lc+no+rc)
    LsColors['ec'] = LsColors['lc'] + LsColors['no'] + LsColors['rc']
end

##
# Format the file size in long output according to options.
#
def fmt_size( size )
    ##
    # In human-readable mode, file sizes will only show a decimal point
    # when less then 10, fitting a 4-character wide field (e.g. 1.2M)
    # This seems to match the behavior of GNU ls.
    #
    kilo = $options[:kilo]  # normally 1024, use 1000 with --si option
    if $options[:human_readable]
        size = if size > 1024**3
            size /= kilo**3.0
            if size >= 10
                "%iG" % size.ceil
            else
                "%0.1fG" % size
            end
        elsif size > kilo**2
            size /= kilo**2.0
            if size >= 10
                "%iM" % size.ceil
            else
                "%0.1fM" % size
            end
        elsif size > kilo
            size /= kilo.to_f
            if size >= 10
                "%iK" % size.ceil
            else
                "%0.1fK" % size
            end
        else
            size.to_s
        end
    else
        size = size.to_s
    end
    return size
end

##
# Format the filename according to options
#
def fmt_name( path, ftype=File.ftype(path), stats=nil )
    return "" unless path  # return empty string if path is nil

    name = File.basename(path)

    ##
    # Print filenames in certain colors if --color option is selected.
    #
    if $options[:color]
        #
        # To prevent errors, check if the file 
        if File.exist?( path )
            #
            # apply colors according to 
            color = if ftype == 'link'
                LsColors['ln']
            elsif ftype == 'directory'
                LsColors['di']
            elsif ftype == 'fifo'
                LsColors['pi']
            elsif ftype == 'socket'
                LsColors['so']
            elsif ftype == 'characterSpecial'
                LsColors['cd']
            elsif ftype == 'blockSpecial'
                LsColors['bd']
            elsif File.setuid?( path )
                LsColors['su']
            elsif File.setgid?( path )
                LsColors['sg']
            elsif File.sticky?( path ) && File.world_writable?( path )
                LsColors['tw']
            elsif File.sticky?( path )
                LsColors['st']
            elsif File.stat(path).nlink > 1
                LsColors['hl']
            elsif File.executable?( path )
                LsColors['ex']
            #
            # File.world_writable doesnt see to be in ruby 1.8, so check
            # ruby version for this.
            elsif RUBY_VERSION.to_f >= 1.9 && File.world_writable?( path )
                LsColors['ow']
            #
            # If the file does not match the above criteria, but its extention
            # is included in the LS_COLORS environmental variable, apply color
            elsif LsColors.include?( '*' + File.extname(path) )
                LsColors[ '*' + File.extname(path) ]
            #
            # Default to fi (file). Normally the terminals normal color,
            # but can be changed by setting it in the LS_COLORS env variable
            else
                LsColors['fi']
            end
        #
        # If the file (or a link's target) does not exist, set as orphaned.
        else
            color = LsColors['or']
        end
        
        #
        # wrap the file name with the color codes
        if color
            name = LsColors['lc'] + color + LsColors['rc'] + name + LsColors['ec']
        end
    end

    ##
    # When in `long' mode, the name of a link also contains the target.
    # The target classify and color formatting will reflect the end target,
    # even when the direct target is another link.
    #
    if $options[:long] && ftype == 'link'
        target = File.readlink(path)
        begin
            target_type = File.ftype(target)
            while target_type == 'link' do
                target_target ||= File.readlink(target_target)
                target_type = File.ftype(target_target)
            end
        rescue
            target_type = 'missing'
        end
        name += ' -> ' + fmt_name(target, target_type)
    #
    # append classify indicators
    elsif $options[:classify]
        if ftype == 'link'
            name += Indicators[ftype]
        elsif ftype == 'directory'
            name += Indicators[ftype]
        elsif Indicators.include?( ftype )
            name += Indicators[ftype]
        elsif File.executable?(path)
            name += Indicators['exec']
        end
    end

    return name
end

##
# Long listing method, showing detailed information about each file/dir
def long_list( listing )
    field_lengths = [ 1, 9, 1, 1, 1, 1, 1, 1 ] # length of each field in long output
    split_listings = []
    total = 0
    listing.each do |file|
        ftype = File.ftype(file)
        parts = case ftype
        when 'link'
            ['l']
        when 'directory'
            ['d']
        when 'characterSpecial'
            ['c']
        when 'blockSpecial'
            ['b']
        when 'fifo'
            ['p']
        when 'socket'
            ['s']
        when 'file'
            ['-']
        when 'unknown'  # not sure what to put if it's unknown, prob `-'
            ['?']
        else            # assume anything else is unknown
            ['?']
        end
        if ftype == 'link'
            stats = File.lstat(file)
        else
            stats = File.stat(file)
        end
        parts.push(("%o" % stats.mode)[-3,3].chars.map{|c|
                Permissions[c.to_i]}.join)
        parts.push(stats.nlink.to_s)
        if $options[:long] == 'numeric'
            parts.push(stats.uid.to_s)
            parts.push(stats.gid.to_s)
        else
            parts.push( Etc::getpwuid(stats.uid).name )
            parts.push( Etc::getgrgid(stats.gid).name )
        end
        parts.push(fmt_size(stats.size))
        parts.push(stats.mtime.strftime("%Y-%m-%d %H:%M"))
        total += stats.size
        parts.push( fmt_name(file, ftype) )

        ##
        # Determine field lengths for long output by setting them to the longest
        # entry in that field.
        parts.length.times do |i|
            field_lengths[i] = parts[i].length if field_lengths[i] < parts[i].length
        end

        split_listings.push( parts )
    end
    
    output = ""
    ##
    # If listing is a directory, print the total size
    #
    if listing.length > 1
        if $options[:human_readable]
            output += "total #{fmt_size(total)}\n"
        else
            output += "total #{total / 1024}\n"
        end
    end
    
    ##
    # format each line
    field_lengths[-1] = -1  # left-justify last field
    unless $options[:long] == 'numeric'
        field_lengths[3] *= -1  # left-justify owner field
        field_lengths[4] *= -1  # left-justify group field
    end
    line_fmt = "%#{field_lengths[0]}s%#{field_lengths[1..-1].join('s %')}s\n"
    split_listings.each{ |parts| output += ( line_fmt % parts ) }

    return output
end

##
# normal listing. Show only file names
# Columns do not match the same ordering style as gnu ls (up-down, left-right),
# instead the order is left->right, then up->down.
#
def short_list( listing )
    output = ""
    if $options[:one]
        listing.each{ |path| output += fmt_name(path) + "\n" }
    else
        ##
        # Don't yet know how to get the actual terminal width, so using the
        # standard width.
        max_columns = 80 #ENV["COLUMNS"].to_i
        #
        # find the width of each column of file names, which will be the
        # longest file name
        col_width = 1
        listing.each do |path|
            path = File.basename(path)
            col_width = path.length if path.length > col_width
        end
        #
        # determin the number of columns and rows(line) by the width of the
        # longest file name
        cols = max_columns / (col_width + 2)  # add two for the space between
        cols = 1 if cols < 1
        rows = listing.length / cols
        
        #
        # now place each file/dir name into neat columns
        l = 0
        while l < listing.length do
            line_txt = []
            line_fmt = []
            cols.times do |c|
                next unless listing[l]
                path_width = File.basename(listing[l]).length
                path = fmt_name( listing[l] )
                ##
                # adjust column width to account for non-printing
                # characters that are present in color mode.
                if path_width < path.length
                    adj_width = col_width + (path.length - path_width)
                else
                    adj_width = col_width
                end
                line_fmt.push "%-#{adj_width}s"
                line_txt.push( path )
                l += 1
            end
            line_fmt = line_fmt.join('  ') + "\n"
            output += line_fmt  % line_txt
        end
    end

    return output
end

##
# Determine whech files and directories to list, then list use appropriate
# method to list them according to the options.
def get_listing( paths=$options[:paths] )
    paths.sort!
    files = [] # will hold non-directories
    dirs  = [] # will hold directories to be listed after files
    paths.each do |path|
        unless File.exist?( path )
            begin
                File.lstat( path )
            rescue
                STDERR.write "#{ProgramName}: cannot access #{path
                        }: No such file or directory\n"
                paths -= [path]
                next
            end
        end
        ##
        # if -d option is not used, list contents of directories
        if File.directory?( path ) && ! $options[:directory]
            listing = Dir.entries( path )
            unless $options[:all]
                listing = listing.map{|p| p unless /^\./ =~ p}.compact
            end
            dirs.push( listing.map{ |p| File.join(path, p) }.sort )
        else
            files.push( path )
        end
    end

    ##
    # Get listings for files then each directory.
    # For some reason, an empty array sometimes gets pushed into dirs, we
    # remove that here as well.
    ([files] + dirs - [[]]).each do |files|
        #
        # print directory name unless its the top or only directory
        #
        unless files.empty? || paths.include?( files[0] ) || dirs.length == 1
            puts "\n" + File.dirname( files[0] ) +":\n" 
        end

        ##
        # Get listing for files
        if $options[:long]
            puts long_list( files )
        else
            puts short_list( files )
        end
    end
end

##
# Get options from command line arguments
#
$options = {
    :kilo=> 1024    # power of bytes for human readable mode. change with --si
}

parse_opts = OptionParser.new do |opts|
    opts.banner = "Usage: #{ProgramName} [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).\n"
    opts.summary_width  = 29
    opts.summary_indent = "  "
    newl = "\n" + " " * opts.summary_width + opts.summary_indent

    opts.on("-l", "use a long listing format") do
        $options[:long] = true
        require 'etc'
    end
    opts.on("-a", "--all", "do not ignore entries starting with .") do
        $options[:all] = true
    end
    opts.on("--color=[WHEN]",
            "control whether color is used to distinguish file#{
            newl}types.  WHEN may be `never', `always', or `auto'") do |colors|
        ##
        # default to `auto'
        colors = 'auto' unless colors

        case colors
        when 'always', 'yes', 'force'
            $options[:color] = true
        when 'never', 'no', 'none'
            $options[:color] = false
        when 'auto', 'tty', 'if-tty'
            $options[:color] = true if STDIN.tty?
        else
            STDERR.write "#{File.basename($0)}: invalid argument `#{colors}' for `--color'
Valid arguments are:
  - `always', `yes', `force'
  - `never', `no', `none'
  - `auto', `tty', `if-tty'
Try `ls --help' for more information.\n"
            exit(1)
        end

        ##
        # parse environmental variable: LS_COLORS
        parse_colors if $options[:color]
    end
    opts.on("-d", "--directory", "list directory entries instead of contents,#{
            newl}and do not dereference symbolic links") do
        $options[:directory] = true
    end
    opts.on("-F", "--classify", "append indicator (one of */=>@|) to entries") do
        $options[:classify] = true
    end
    opts.on("-h", "--human-readable",
            "with -l, print sizes in human readable format#{newl}(e.g., 1K 234M 2G)") do
        $options[:human_readable] = true
    end
    opts.on("--si", "likewise, but use powers of 1000 not 1024") do
        $options[:kilo] = 1000
    end
    opts.on("-n", "--numiric-uid-gid", "like -l, but list numeric user and group IDs") do
        $options[:long] = "numeric"
    end

    opts.on("-1", "list one file per line") do
        $options[:one] = true
    end
    
    opts.on("--help", "display this help and exit") do
        puts opts.banner + "\n"
        puts opts.summarize( [], 26 )
        exit
    end

end

begin
    parse_opts.parse!
rescue OptionParser::InvalidOption => e
    STDERR.write "#{ProgramName}: #{e}\n"
    STDERR.write "try #{ProgramName} --help for more info.\n"
    exit(1)
end

##
# Get paths to list from remaining arguments
#
$options[:paths] = []
ARGV.sort.each{ |arg| $options[:paths].push(arg) }
$options[:paths].push('.') if $options[:paths].empty?

##
# Get the listing
#
get_listing($options[:paths])
```

---

### Post by texaswriter on 2010-05-31
Here is my latest code. The functions, -F -h -a -l work as intended. I do have -R programmed in, but disabled it due to an unknown glib memory error. Valgrind doesn't detect anything, so not sure about that. Also, in some cases, passing too many directories as arguments will cause weird glib memory issues. Once again, Valgrind doesn't detect anything, so not sure about that either. As far as I am concerned, all these are ridiculous. If the function that processes the individual paths runs ONCE FINE AND gets called a second time, it should run fine as well. 

Needless to say: compilation instructions; gcc -x c -lm name.c -o name

not sure if -lm is fine. You can do -Wall as well, I think there are just two variables I never used that I forgot to delete.... 

Once again, if you see any show-stopping errors, please let me know and any thoughts and comments are welcome. 

Like I said though, it does what it's supposed, more or less. That said, I'm NEVER getting directory information myself... 

Enjoy!!!


[PHP]
/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
/*
 * main.c
 * Copyright (C) texaswriter 2010 
 * 
 * LS_replacement is free software: you can redistribute it and/or modify it
 * under the terms of the GNU General Public License as published by the
 * Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 * 
 * LS_replacement is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * See the GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License along
 * with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

const int malloc_step = 15;
const char *dir_dot1 = ".\0";
const char *dir_dot2 = "..\0";
const char *dir_root = "/\0";

#include <stdio.h>
#include <ctype.h>
#include <unistd.h>
#include <string.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <dirent.h>
#include <errno.h>
#include <pwd.h>
#include <grp.h>


//Global variables are BOTH AWESOME and EVIL
int input_flags[10]; //holds options flags

//Creates the full path from the path and the filename and passes it back in a pointer
char *path_build(char *path, char *concat);

//Handles checking the type of file
char append_type(struct stat st, char *path);

//appends proper character to filename/directory name/etc
char name_append(char *path);

//prints the file size according to input options
void size_append(int fsize);

//Skeleton for workhouse function
//int texas_ls(char *path, );

//skeleton for *new* workhouse function
int tx_ls(char *path);

//Displays any needed error messages
void texas_error(int errcode);

int main(int argc, char *argv[])
{
    //struct dirent *dir_buffer; //directory structure #1
//    char *input_path; //input buffer for path
    char **directory_path=NULL; //This will hold all the input directories to cycle through
    int max_dp=0;
    int input_options; //holds temporary input from getopt()
    int i,j;//,k; //Random loop variables
    int counter_flag=0; //holds number of flagged options

    directory_path=malloc(argc*sizeof(*directory_path));   //Allocates for pointer array

    //error trapping
    if(directory_path==NULL)    {   
        printf("\n\nFatal Error: %d\n", errno);  
        return 1; 
    } 
  
    while((input_options=getopt(argc, argv, "aFhlR"))!=-1) //processes options
    {
        counter_flag++;    
        switch(input_options)
        {
              case 'a':      input_flags[0]=1; break;  //-a --all
              case 'F':      input_flags[1]=1; break;  //-F --classify append */=>@| to entries
              case 'h':      input_flags[2]=1; break;  //-h --human-readable 
              case 'l':      input_flags[3]=1; break;  //-l long listing format
              case 'R':      input_flags[4]=0; break;  //-R --recursive list subdirectories recursively
              case '?':      {
                  printf("\n\nUnknown option, directory read aborted!!\n\n"); 
                  return 1;      
              }
        }
    }
    
    //Will go through all the options and extract the possible directory entries: For parsing of multiple directories
    //For anybody wondering why I even bother saving this, this is a *beginner programming exercise* or should be anyways
    //and this helps me learn about malloc 
    for(i=argc-1, j=0; i>0; i--)
    {
        if(argv[i][0]!='-')
        {   
            if(!(directory_path[j]=malloc(strlen(argv[i])+1)))  {
                printf("\n\nFATAL ERROR: %d\n", errno);   
                return 1; 
            } 
            strcpy(directory_path[j],argv[i]);
            j++;
        }
            
    }
    
    max_dp=j;

    //Starts processing the directories: 
    if(max_dp>0)    {
        for(i=0; i<max_dp; i++) {
            j=tx_ls(directory_path[i]); 
            texas_error(j);
        }    
    }
    else    {
        j=tx_ls(".\0");    
        texas_error(j);
    }
    
    //frees array of pointers    
    for(i=0; i<argc; i++)    
        if(directory_path[i]!=NULL) 
            free(directory_path[i]);
    
    if(directory_path!=NULL) free(directory_path); //frees pointer

    //if(input_path!=NULL)    {   free(input_path);   }

    return 0;
}

//This implementation of the workhorse function will put *ALL* the data into an array of strings before printing, this way the function can be consolidated a bit more
//It will also assist in the case statements as well as the 
int tx_ls(char *path){
    DIR *dp;            //directory variables
    DIR *dp2;            //extra directory...
    struct dirent *dirp;
    struct stat st;

    char **storage=NULL;        //This will hold the filenames/directory names. 
//    char **directories;
    char *tmp=NULL;            //holds temporarily
    char *tmp2=NULL;
    char appendc;
    struct group *grp;  //
    struct passwd *pwd; //
        
    int i=0,j=0,k=0;            //your typical loop variables
    int max_s=0;//, max_d=0;       //stores the max size of the arrays

    //dp=NULL;

    printf("\n%s:\n",path);

    storage =  malloc(malloc_step*sizeof(*storage));
    if(!storage)  {
        printf("\n\nFATAL ERROR: %d\n\n",errno);
        return errno;
    }
    max_s+=malloc_step;

    if((dp=opendir(path))==NULL)    {
        printf("\n\nFATAL ERROR: %d\n\n",errno);
        return -1;
    }
    
    while((dirp=readdir(dp)))    {
        if((input_flags[0]==0)&&(dirp->d_name[0]=='.'))
            continue;
        else        {
            storage[i] = malloc(strlen(dirp->d_name)+2);
            strcpy(storage[i], dirp->d_name);
            i++;
            
            if(i==max_s)   {
                max_s+=malloc_step;
                storage = realloc(storage, max_s*sizeof(*storage));
                if (storage==NULL)  {
                    printf("\n\nFATAL ERROR: %d\n\n",errno);
                    return errno;
                }
                
            }
            
        }
    }
    
    //This series of if statements will print the data according to the requested format. Please note that a small bit of code duplication occur to facilitate a cleaner loop. 
    if(input_flags[3]==1)   /*-l printing processing*/     {
        for(j=0; j<i; j++)        {
            
            
            
            tmp=path_build(path, storage[j]); //builds the directory path properly
            if(tmp==NULL) continue;              //if tmp returned null, "." or ".." was the path

            

            if(lstat(tmp, &st)==-1) 
                printf("\n\nLSTAT ERROR: %d\n\n",errno);
            else    {
                pwd=getpwuid(st.st_uid);
                grp=getgrgid(st.st_gid);
            
                if(input_flags[1]==1)
                    appendc=append_type(st, path);
                else 
                    appendc=' ';
                
                printf("%04o %18s %18s ", (int) st.st_mode&4095, pwd->pw_name, grp->gr_name);
                size_append( (int) st.st_size);
                printf("%s%c\n", storage[j], appendc);
                if(tmp!=NULL) free(tmp);
            }
        }
            
            
        
    }
    else     {                //normally prints directories
        for(j=0; j<i; j++)  {
            //tmp=malloc(strlen(storage[j])+strlen(path)+20);
            tmp=path_build(path, storage[j]);
            
            if(lstat(tmp, &st)==-1) {
                //printf("lstat erro: %d",errno);
            }
            else    {
            
               

                if(input_flags[1]==1)
                    appendc=append_type(st, path);
                else 
                    appendc=' ';
            
                if(strlen(storage[j])<19)   {
                
                    printf("%19s%c",storage[j], appendc);
                }
                else        {
                    if(((j+1)%4)>3)
                        printf("\n");
                    printf("%39s%c", storage[j], appendc);
                }

            }
            if(tmp!=NULL) free(tmp);
                
        }
    }

    if(input_flags[4]==1)    {
        for(j=0; j<i; j++)        {

            lstat(storage[j],&st);
            
            if(S_ISDIR(st.st_mode))            {

                tmp=path_build(path, storage[j]);

                k=tx_ls(tmp);
                if(tmp!=NULL) free(tmp);
            }
        }
    }
    
    for(j=0; j<max_s; j++)  //frees stored names
        if(storage[j]!=NULL)    free(storage[j]);
    if(storage!=NULL) free(storage);
        
    if(dp!=NULL) closedir(dp);
    //if(path!=NULL) free(path);
      
    return 0;
}
void texas_error(int errcode)
 {
     switch(errcode)
     {
         case -1:   printf("\n\n***** Directory couldn't be opened or does not exist. *****\n\n");   break;
         case  0:   {}  break;
         default:   {} 
     }
     return;
 }

char append_type(struct stat st, char *path)
{
    lstat(path, &st);

    if(S_ISREG(st.st_mode))            {
        //closedir(dp);
        return ' ';
    }
    else if(S_ISDIR(st.st_mode))    {
        //closedir(dp);
        return '/';
    }
    else if(S_ISLNK(st.st_mode))    {
        //closedir(dp);
        return '@';
    }
    else if(S_ISCHR(st.st_mode))    {
        //closedir(dp);
        return ' ';
    }
    else if(S_ISBLK(st.st_mode))    {
        //closedir(dp);
        return ' ';
    }
    else if(S_ISFIFO(st.st_mode))   {
        //closedir(dp);
        return '|';
    }
    else if(S_ISSOCK(st.st_mode))   {
        //closedir(dp);
        return '=';
    }
    else if((st.st_mode&S_IXOTH)||(st.st_mode&S_IXGRP)||(st.st_mode&S_IXUSR))   {
        //closedir(dp);
        return '*';
    }
    else    {
        //closedir(dp);
        return ' ';
    }
}

void size_append(int fsize)
{
    if(input_flags[2]==1)   {
        if((fsize/1024)<1024)
            printf("%6.2f Kb ", ((double)fsize/1024));
        else if((fsize/(1024^2))<(1024))
            printf("%6.2f Mb ", ((double)fsize/(1024^2)));
        else if((fsize/(1024^3))<(1024))
            printf("%6.2f Gb ", ((double)fsize/(1024^3)));
        else if((fsize/(1024^4))<(1024))
            printf("%6.2f Tb ", ((double)fsize/(1024^4))); //Yeah, we are future proofing this :-D
    }
    else
            printf("%8d    ", fsize);

    return;
    
}

char *path_build(char *path, char *concat)
{
    char *tmp;
    tmp=malloc(strlen(concat)+strlen(path)+3);
    if(!tmp)    {
        printf("\n\nFATAL ERROR: %d\n\n", errno);
        return NULL;
    }

    if((path[0]=='/')&&(strlen(path)==1))  {
        strcpy(tmp,path);
        strcat(tmp, concat);
    }
    else {
        strcpy(tmp, path);
        strcat(tmp, "/\0");
        strcat(tmp, concat);
    }
    
    return tmp;
}

[/PHP]

---

### Post by Bodsda on 2010-06-01
Evening fellow coders. As this challenge seems to have been abandoned by its poster, and as the sponsors of these challenges, the Ubuntu Beginners Team Development Focus Group has taken over the judging. 

The winner of this challenge is.................

[Texaswriter]("http://ubuntuforums.org/member.php?u=997976")!!!

!*!CONGRATULATIONS!*!

Texaswriter's well commented and easily readable code has earned him a place in the Ubuntu Beginner Programmers Hall Of Fame. Although his code was not as feature rich as some others, his constant debugging efforts showed determination and skill that is needed for any aspiring programmer.

I invite you to post challenge #13, entitled "Beginner's Programming Challenge #13". As always, please try and emphasise the rules and criteria in your opening post. I look forward to seeing the challenge.

To anyone still coding, please feel free to post your solutions. Although they will not be judged, you may get some feedback on your code.

Happy Coding,
Bodsda

---

### Post by AdotB on 2010-06-01
'Grats Texaswriter!

---

### Post by texaswriter on 2010-06-01
Thanks!! :popcorn::guitar::KS

The next challenge is live: 

[http://ubuntuforums.org/showthread.php?t=1500005](http://ubuntuforums.org/showthread.php?t=1500005)

Good Luck!!!

---

### Post by texaswriter on 2010-07-01
In case this is helpful to anyone: I found out the source of my elusive "bug". It is not really a bug in any sense... Like I had said, I ran my program through Valgrind and it detected *nothing*. But running the following code: export MALLOC_CHECK_=0  
before you execute a program that crashes with an error similar to this: glibc detected export double free or corruption (top):

will solve that problem. 

That's good news.... I really don't understand why it would be a problem... I have thoroughly checked my free() statements... It very specifically checks to see if it is null before freeing... 

Anyways... I hope that the above is useful to somebody.

---

### Post by StephenF on 2010-07-02
> **texaswriter said:**
> In case this is helpful to anyone: I found out the source of my elusive "bug". It is not really a bug in any sense... Like I had said, I ran my program through Valgrind and it detected *nothing*. But running the following code: export MALLOC_CHECK_=0  
before you execute a program that crashes with an error similar to this: glibc detected export double free or corruption (top):

will solve that problem. 

That's good news.... I really don't understand why it would be a problem... I have thoroughly checked my free() statements... It very specifically checks to see if it is null before freeing... 

Anyways... I hope that the above is useful to somebody.
If you have to set MALLOC_CHECK_ your memory management *is* messed up.

You are allocating and reallocating the storage array in blocks of malloc_step without setting the internal values to NULL so when you get to the freeing you end up calling free on memory that was never allocated in the first place yet you have at your disposal variable 'i' containing the exact number of elements in use and could have used it to good effect in your free loop.

The directory_path variable is similarly afflicted and uses a scheme so similar that the mechanism ought to have been abstracted out to avoid repetition. See the code below which is suitable for reuse in other programs. Usage should be obvious.

Untested.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct char_vec
    {
    char **data;       /* data[0], data[1], ..., data[elements - 1] */
    size_t elements;   /* exact number of elements */
    size_t block_size; /* number of elements in an allocation unit */
    };
    
struct char_vec *char_vec_new(size_t block_size)
    {
    struct char_vec *s;
    
    if (!(s = malloc(sizeof (struct char_vec))))
        {
        printf("malloc failure\n");
        exit(5);
        }
        
    if (!(s->data = malloc(block_size * sizeof *s->data)))
        {
        printf("malloc failure\n");
        exit(5);
        }
        
    s->elements = 0;
    s->block_size = block_size;
    s->data[0] = NULL;
    
    return s;
    }
    
void char_vec_free(struct char_vec *s)
    {
    char **dp = s->data;
    size_t e = s->elements;
    
    while (e--)
        free(*dp++);
    
    free(s->data);
    s->data = NULL; /* Future calls to grow or free will segfault. */
    free(s);
    }
    
void char_vec_grow(struct char_vec *s, const char *new_data)
    {
    /* The extra space is for the NULL terminator. */
    size_t blocks = (s->elements + 1) / s->block_size + 1;
    size_t needed = (s->elements + 2) / s->block_size + 1;
    
    if (needed > blocks)
        {
        s->data = realloc(s->data, needed * s->block_size * sizeof *s->data);
        if (!s->data)
            {
            printf("malloc failure\n");
            exit(5);
            }
        }
        
    s->data[s->elements++] = strdup(new_data);
    s->data[s->elements] = NULL;
    }

```

---

### Post by texaswriter on 2010-07-03
Thanks for that. I'll check it out and see if I can fix that in the original program. Otherwise, I'll keep those subroutines in mind. 

:guitar::popcorn::KS:popcorn::popcorn::KS:KS

---

### Post by wkhasintha on 2010-07-04
Im on it

---

### Post by CuracaoThe on 2011-08-03
Written in Ruby language:
[PHP]
# Warning! Not precise implementation due to my coding ability.

require 'optparse'
require 'ostruct'
require 'etc'

=begin

  The purpose of this class is to parse command line arguments.
    
=end

class CommandLineParser

  # Parse all command line arguments.
  #
  def self.parse(args)
    options = OpenStruct.new

    # Columns is a -C (not implemented) flag. It's default flag.
    options.columns = false

    # Long is a -l or --long flag.
    options.long = false

    # All is an -a or --all flag.
    options.all = false

    # Classify is a -F or --classify flag.
    options.classify = false

    # Human readable is a -h or --human-readable flag.
    options.readable = false

    # The very arguments handling.
    opts = OptionParser.new do |opts|
      opts.banner = "List directory contents.\n"\
                    "Usage: ./ls.rb [OPTIONS]... [FILE]..."
      opts.separator ""

      opts.on("-l", "--long", "Use a long listing format.") do |long|
        options.long = long
      end

      opts.on("-a", "--all", "Do not ignore entries starting with '.'.") do |all|
        options.all = all
      end

      opts.on("-F", "--classify",
              "Append indicator (one of */=>@|) to entries.") do |classify|
        options.classify = classify
      end
      
      opts.on("-h", "--human-readable",
              "With -l, print sizes in human readable format",
              "(e.g., 1K 234M 2G).") do |readable|
        options.readable = readable
      end

      # Default path
      options.path = "."

      opts.on_tail("-p", "--path PATH", String,
              "Set the directory to show it contents") do |path|
        options.path = path
      end

    end

    # Parse command line arguments.
    opts.parse!(args)

    # If no arguments given (when every option is equal to 'false'),
    # use -C flag as a default.
    options.columns = true unless options.marshal_dump.values.include?(true)

    # Return Hash object as a result of parsing.
    options.marshal_dump
  end

end

=begin
  
  Ruby implementation of Linux console utility 'ls'.

=end

class Ls

  def list
    with_option = CommandLineParser.parse(ARGV)
    out = []

    Dir.entries(with_option[:path]).sort.each do |file|
      # Default option handling (when no arguments provided).
      next if file.start_with?(".") and with_option[:columns]

      # Change working directory.
      Dir.chdir(with_option[:path])

      if File.directory?(file) and with_option[:classify]
        next if file.start_with?(".") and not with_option[:all]
        file.concat("/") 
      end
    
      if with_option[:long]
        next if file.start_with?(".") unless with_option[:all]

        # Container of long notation string.
        long = []

        # File's permissions.
        permissions = sprintf("%o", File.stat(file).mode)
        long << permissions

        # Quantity of hard links to a file.
        nlink = File.stat(file).nlink
        long << nlink

        # Owner of a file.
        uid = File.stat(file).uid
        owner = Etc.getpwuid(uid).name
        long << owner

        # An owner's group.
        group = File.stat(file).gid
        long << group

        # File's size.
        size = File.size(file)
        size = to_k(size) if with_option[:readable]
        long << size

        # The last time, when file was accessed by someone.
        ctime = File.ctime(file)
        long << ctime.strftime("%b %e")
        
        # Filename.
        file = long << file

        # Actual string to output.
        file = file.join(" ")
      end

      out << file
    end

    puts out
    nil
  end
  
  private

  def to_k(bytes)
    Float(bytes / 1024).to_s + "K"
  end

end

print Ls.new.list
[/PHP]

---

