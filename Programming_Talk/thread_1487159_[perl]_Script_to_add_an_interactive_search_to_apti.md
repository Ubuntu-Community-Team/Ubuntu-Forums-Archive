---
title: "[perl] Script to add an interactive search to aptitude"
date: 2010-05-18
forum: Programming Talk
---

### Post by wimille on 2010-05-18
Hi,
I'm trying to develop a perl script to add an interactive search to aptitude (in CLI).

This script shows the result of a search with aptitude and allows to the user to choose any packages he wants to install among the results.

For now, the script is in French (my native language) but the picture is the same with other languages :

[IMG]http://beware007.free.fr/aptinter.jpg[/IMG]

Now, for those who are interested :
 - [Direct link]("http://beware007.free.fr/aptinter.pl")

 - [svn web page of my script]("http://beware.homelinux.org/filedetails.php?repname=Scripts&path=%2FAptinter%2Faptinter")

At last, every comments or critics is welcome.

PS : currently, i'm going to translate the script in English.

---

### Post by nvteighen on 2010-05-19
Sorry, but I don't see the difference with aptitude's built-in search facility on full-screen mode. Care to explain it a bit more?

Anyway, please **remove all calls to sudo**. This is a security critical issue. All calls to sudo should be done explicitly by the user, never automatically by a program; the user has to know when he's going to act as root and when not and if sudo was used before and the timeout hasn't expired yet, there'll be no prompting for password. So, use system "aptitude ..." and that way the user will have to execute aptinter with sudo explicitly to make it work. (btw, this will also help you to make your script be useful for people that use su instead of sudo, like almost all Debian users like me!)

---

### Post by wimille on 2010-05-19
Thank you for your comment.

First, what's the aptitude's built-in search facility on full-screen mode ? I've already used aptitude in console mode.

Secondly, you're right. Use sudo is not a good idea, because it's restricted to ubuntu users. Now, i've used "su -c 'aptitude....'" instead. It's better no?.  At last, i had not think about security of the script, thank you for the advices.

EDIT: i've finished the translation of the script (first issue).

---

### Post by nvteighen on 2010-05-19
> **wimille said:**
> 
First, what's the aptitude's built-in search facility on full-screen mode ? I've already used aptitude in console mode.


Enter:
```

aptitude

```

A so-called "full-screen mode" interface will be launched; they call it that way on aptitude's documentation... it's what one could call a "TUI" (text user interface), i.e. a "GUI" based on text...

In that mode, hitting / or using the menus will start the search facility.

> 
Secondly, you're right. Use sudo is not a good idea, because it's restricted to ubuntu users. Now, i've used "su -c 'aptitude....'" instead. It's better no?.  At last, i had not think about security of the script, thank you for the advices.


No, that's the same. In your code, just do **system "aptitude ..."**. That way, if the user wants to use your script as root, he'll have to use **sudo aptinter ...** or **su -c "aptinter ..."**... or login as root if he likes; if you do what I suggest, you'll give the user the freedom to choose the method he likes to use to get root privileges and not force anyone to configure sudo. Running your script as root will make aptitude work as root as well; the thing is the user has to know when something is running as root an when not and the best way to do it is to ask the user to get root privileges. When not run as root, your script will fail when aptitude tries to install something, spitting out a permissions error... but, for searching, you don't need to be root (try "aptitude search" without sudo!), so it will work for that.

A nice feature would be that the install prompt appeared only when the user is root. For that **if($ENV{USER} eq 'root'){...}** would be enough in Perl.

> 
EDIT: i've finished the translation of the script (first issue).
:)

---

### Post by wimille on 2010-05-20
Thank you for your explanation about su and sudo. Now, i well understood.

Thanks for your idea to use '$ENV{USER}...', now i can control if the script has root privileges or not, and if not, warn the user. And so i don't used sudo or su anymore in my script.

Secondly, i tried 'aptitude' in full-screen mode as you say, but, in my opinion, it's a little complicated for a quick search of a package. I think my script is faster and easier to use on this point. But i can be wrong.

---

### Post by nvteighen on 2010-05-20
> **wimille said:**
> 
Secondly, i tried 'aptitude' in full-screen mode as you say, but, in my opinion, it's a little complicated for a quick search of a package. I think my script is faster and easier to use on this point. But i can be wrong.

Ok, it's a good point. Good luck!

---

### Post by shawnhcorey on 2010-05-21
> **nvteighen said:**
> A nice feature would be that the install prompt appeared only when the user is root. For that **if($ENV{USER} eq 'root'){...}** would be enough in Perl.

Actually, you should use the real UID (see `[perldoc perlvar]("http://perldoc.perl.org/perlvar.html")` and search for /REAL_USER_ID/).

```
if( $< == 0 ){  # 0 is the root uid
```

---

### Post by wimille on 2010-05-22
Sorry, for my late answer. 
First, thank you for your comment. 
I've modified my script to user perlvar (which i didn't knew).

---

### Post by shawnhcorey on 2010-05-22
> **wimille said:**
> Sorry, for my late answer. 
First, thank you for your comment. 
I've modified my script to user perlvar (which i didn't knew).

In that case, you should check out these as well:
perldoc perl
perldoc perlop
perldoc perlfunc

---

### Post by wimille on 2010-05-25
Hi all,

I've made some changes on my script.

I created a new function in order to simplify the script (well i hope).

```

#!/usr/bin/perl
################################################################################
#  Perl Script :                                                               #
#                                                                              #
#                            Interactive Search Aptitude                       #
#                                   aptinter                                   #
#                                                                              #
################################################################################
#                                                                              #
#  DATE    : 05-25-2010                                                        #
#  AUTHOR  : M.Hedard <mathieu.hedard@gmail.com>                               #
#  VERSION : 0.3                                                               #
#                                                                              #
################################################################################
#                                                                              #
# But : The script allows to make an interactive search in the package         #
#       database with aptitude. Most, it allows to install packages directly   #
#       from the search results.                                               #
#                                                                              #
################################################################################
# Licence :                                                                    #
#                                                                              #
# aptinter - Search and Install a package quickly and easily                   #
#                                                                              #
# Copyright (C) 2010  M.Hedard                                                 #
#                                                                              #
# This program is free software: you can redistribute it and/or modify         #
# it under the terms of the GNU General Public License as published by         #
# the Free Software Foundation, either version 3 of the License, or            #
# any later version.                                                           #
#                                                                              #
# This program is distributed in the hope that it will be useful,              #
# but WITHOUT ANY WARRANTY; without even the implied warranty of               #
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the                #
# GNU General Public License for more details.                                 #
#                                                                              #
# You should have received a copy of the GNU General Public License            #
# along with this program.  If not, see <http://www.gnu.org/licenses/>.        #
#                                                                              #
################################################################################

use strict;
use warnings;
use Getopt::Long;
use English '-no_match_vars';
Getopt::Long::Configure( "no_auto_abbrev" );

# Constant used by script : 
#     field number in search result array (0-3)
#     number of informations (4)
use constant {
   PACK_STATE => 0,
   PACK_NAME  => 1,
   PACK_VERS  => 2,
   PACK_SIZE  => 3,
   PACK_DESC  => 4,
   NB_INFOS   => 5,
};

# The function checks the length of the text and return the text if the length
# is not null. Else, it returns '-'.
sub check_field($)
{
   my $text = shift;
   if( $text )
   {
      return $text;
   }
   else 
   {
      return "-";
   }
}

# To use full options of the script root privileges are required
# the perlvar $< is the real processus id (0 is root)
if( $< != 0 )
{
   print "  Warning : You need root privileges to use the script\n";
}
else
{
   # If none patterns supplied, the script ends
   if ( scalar @ARGV == 0 )
   {
      print "  Failed : You have not supply any pattern for the research\n";
   }
   # Only one pattern is allowed
   elsif ( scalar @ARGV > 1 )
   {
      print "  Failed : Only one pattern is allowed\n";
   }
   # Else we can execute the main part
   else
   {
      # We perform a research with the user pattern. The display format for the
      # search result is :
      # pack_state pack_name candidate_version pack_size pack_description
      my $pattern = $ARGV[0];
      my $res = `aptitude search -F "%c@%p@%V@%D@%d" --disable-column $pattern`;
   
      # If there is no result, the script ends
      if ( length( $res ) != 0 )
      {
         # We put the search result in an array to separate each field
         our @search_array = split( /[@\n]/, $res );
   
         # Display the search result like :
         # package_number  package_state  package_name
         # candidate_version
         # package_description
         my $pack_number = 0;
         my $line_number = 1;
         print "\n";
         while ( $pack_number < $#search_array )
         {
            # Array which stores all information of a package
            my @package_infos;

            # We use $i to count each find packages and we use $i to number
            # each field of package informations
            # $pack_number =  4 * $field 
            my $field = $pack_number;
   
            # We check if the field is empty or not. If empty, we put "-"
            # instead by using the funciton check_field
            while ( $field < $pack_number + NB_INFOS )
            {
               $package_infos[$field] = check_field( $search_array[$field] );
               $field++;
            }
           
            # We print the result of each lines
            print "  ".$line_number++."\t"
                      .$package_infos[PACK_STATE + $pack_number]
                      ."  \033[1;37m"
                      .$package_infos[PACK_NAME  + $pack_number]
                      ."\033[0m "."\033[1;33m["
                      .$package_infos[PACK_VERS  + $pack_number]
                      ."]\033[0m "."\033[1;31m["
                      .$package_infos[PACK_SIZE  + $pack_number]
                      ."]\033[0m\n"."\t   "
                      .$package_infos[PACK_DESC  + $pack_number]
                      ."\n";

            # We jump to next package. Now field is set on the first field
            # of the next package.
            $pack_number = $field;
         }

         # We ask the user which package(s) he wants installed. The numbers of
         # packages must be separated by a space. We delete the new line
         # character at the end of the list.
         my $user_input;
         do
         {
            print "\n ==> Package(s) to install :\n".
                  " (To install multiple packages, enter the numbers separated".
                  " by a space. To quit press enter.)\n".
                  " Number(s) : ";
            $user_input =  <STDIN>;
            chomp ($user_input);
         }
         while ( $user_input =~ /[a-zA-Z_]/ );

         # We put all numbers in an array and then we treat them only if one or
         # more numbers have been given by the user.
         #
         # The package name corresponding to the number is determinated like
         # that :
         #  - we subtact 1 because the array started at 0
         #  - there is 5 fields on each line of search result, then we multiply
         #     by 5 to get the correct line
         #  - we add 1 because, the package name is on the second field on the
         #     line
         if ( $user_input !~ /^$/ )
         {
            my @pack_array = split(/[,\W]/,$user_input);
            my @pack_install;
            foreach my $t (@pack_array)
            {
              push( @pack_install, 
                    "$search_array[($t-1) * NB_INFOS + PACK_NAME] " );
            }
            
           # Now we can install all wanted pacakges
           print "\n";
           system "aptitude install -y @pack_install";
         }
      print "\n";
      }
   }
}

```

Edit: Well, i've make a mistake. So i changed the code. Also, now the size of package is available.

---

