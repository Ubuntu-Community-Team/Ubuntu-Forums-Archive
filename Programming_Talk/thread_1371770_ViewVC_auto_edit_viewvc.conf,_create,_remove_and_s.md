---
title: "ViewVC auto edit viewvc.conf, create, remove and svnadmin..."
date: 2010-01-03
forum: Programming Talk
---

### Post by iMisspell on 2010-01-03
Hello all...

Recently ive installed Subversion and then later ViewVC for my own personal use. While looking for an easy way to Create new repositories in svn and also add that to ViewVC i created two bash scripts (and thought i would share), one will create the other will remove.

Im new to bash scripting (and svn and Viewvc) so im sure there are better ways to go about this. I searched for a few minutes and did not find anything so i wrote these.

You opinion is welcome.

Full description:
_[http://wiki.joescove.com/Auto_create_new_Subversion_repository_and_New_entries_in_ViewVC_viewvc.conf](http://wiki.joescove.com/Auto_create_new_Subversion_repository_and_New_entries_in_ViewVC_viewvc.conf)_
Creating new repository 

```

#!/bin/bash

# *** CONFIG SETTINGS - Change to reflect your environment ***
#
# path where 'viewvc' is installed
viewvc_config_path='/usr/local/viewvc-1.0.9';
#
# root path where Subversion saves its repositories
SVNpath='/all/mySubversion';
#
# Filesystem to be used for SVN
# 1 = FSFS
# 0 = Berkeley DB-based
svnFileSystem_fsfs='1';
#
# Owner name for newly created svn repo dir
OwnName='root';
# Group name name for newly created svn repo dir
GroupName='subversion';
#
# *** END OF CONFIG ***


# used for backing up 'viewvc.conf' file
NOW=$(date +"%Y-%m-%d");

# print to tty
echo 'New svn repository name=';
# get results, save to 'RPOname' var
read RPOname;

# exit - if no name is created
if [[ $RPOname == '' ]] ; then
exit;
fi

echo "New repository name will be $RPOname";

sudo mkdir "$SVNpath/$RPOname";
echo '-> mkdir ' "$SVNpath/$RPOname";

sudo chown -R "$OwnName:$GroupName" "$SVNpath/$RPOname";
echo '-> chown -R ' "$OwnName:$GroupName" "$SVNpath/$RPOname";

sudo chmod 0777 -R "$SVNpath"
echo '-> chmod 0777 -R' "$SVNpath";


if [[ $svnFileSystem_fsfs == 1'' ]] ; then
   svnadmin create "$SVNpath/$RPOname"  --fs-type fsfs;
   echo '-> svnadmin create' "$SVNpath/$RPOname"  --fs-type fsfs;
else
   svnadmin create "$SVNpath/$RPOname";
   echo '-> svnadmin create' "$SVNpath/$RPOname";
fi



# print to tty - Named used for ViewVC
echo 'ViewVC name=';
# get results, save to 'ViewVCname' var
read ViewVCname;

if [[ $ViewVCname != '' ]] ; then
   # need to excape / with \/ for the sed replace
   SVNpath=${SVNpath//\//\\/};
   
   # change to ViewVC's dir
   cd "$viewvc_config_path"
   # Backup viewvc.conf with SVN dir name and date
   sudo cp viewvc.conf viewvc.pre."$RPOname.$NOW"

   # replace 'svn_roots = ' and 'root_parents = ' with the new names and paths
   sudo sed -i "s/svn_roots \= /svn_roots \= $ViewVCname \: $SVNpath\/$RPOname , /" viewvc.conf
   sudo sed -i "s/root_parents \= /root_parents \= $SVNpath \: $ViewVCname , /" viewvc.conf
   
   
   viewvc=$(cat "$viewvc_config_path/viewvc.conf" | egrep '^svn_roots |/\#');
   echo '--------- ViewVC svn_roots ---------'
   echo "$viewvc";
   echo '------------------------------------'


   viewvc=$(cat "$viewvc_config_path/viewvc.conf" | egrep '^root_parents |/\#');
   echo '--------- ViewVC root_parents ---------'
   echo "$viewvc";
   echo '------------------------------------'
   
fi

exit; 

```

Full description:
_[http://wiki.joescove.com/Auto_delete_Subversion_repository_and_ViewVC_viewvc.conf_entries](http://wiki.joescove.com/Auto_delete_Subversion_repository_and_ViewVC_viewvc.conf_entries)_
Removing repository 
```

#!/bin/bash


# *** CONFIG SETTINGS - Change to reflect your environment ***
#
# path where 'viewvc' is installed
viewvc_config_path='/usr/local/viewvc-1.0.9';
#
# root path where Subversion saves its repositories
SVNpath='/all/mySubversion';
#
# *** END OF CONFIG ***


NOW=$(date +"%Y-%m-%d");

echo '';
echo '******   SVN Repository List   ******';
# List off all DIR's in SVN's root (for easy copy/paste at next promt);
ls -l "$SVNpath";
echo '';

# Enter the DIR of the repository which you want to delete
echo 'DELETE svn repository';
read RPOname;

# rm the dir
if [[ $RPOname != '' ]] ; then
   sudo rm -R "$SVNpath/$RPOname";
fi

# Print "Subversion roots (repositories)" entry from viewvc.conf
viewvc=$(cat "$viewvc_config_path/viewvc.conf" | egrep '^svn_roots |/\#');
# clean the print alittle
viewvc=${viewvc/svn_roots = /};
viewvc=${viewvc/svn_roots =/};
viewvc=${viewvc/svn_roots= /};
viewvc=${viewvc/svn_roots=/};
echo '--------- ViewVC svn_roots ---------';
echo "$viewvc";
echo '------------------------------------';

# enter what you want to delete, MUST be exact
echo 'DELETE svn_roots =';
read viewvcname;
echo '';

if [[ $viewvcname != '' ]] ; then
   
   viewvcname=${viewvcname//\//\\/};
   viewvcname=${viewvcname//:/\\:};

   # exit ViewVC
   cd "$viewvc_config_path";
   sudo cp viewvc.conf viewvc.pre."$RPOname.$NOW";
   
   sudo sed -i "s/$viewvcname//" viewvc.conf
   
   
   # Print "Subversion root_parents (repositories)" entry from viewvc.conf
   viewvc='';
   viewvc=$(cat "$viewvc_config_path/viewvc.conf" | egrep '^root_parents |/\#');
   viewvc=${viewvc/root_parents = /};
   viewvc=${viewvc/root_parents =/};
   viewvc=${viewvc/root_parents= /};
   viewvc=${viewvc/root_parents=/};
   echo '--------- ViewVC root_parents ---------';
   echo "$viewvc";
   echo '------------------------------------';
   
   viewvcname='';
   # enter what you want to delete, MUST be exact
   echo 'DELETE root_parents =';
   read viewvcname;
   echo '';

   if [[ $viewvcname != '' ]] ; then
      
      viewvcname=${viewvcname//\//\\/};
      viewvcname=${viewvcname//:/\\:};

      # exit ViewVC
      #cd /usr/local/viewvc-1.0.9
      sudo cp viewvc.conf viewvc.pre."$RPOname.$NOW"
      sudo sed -i "s/$viewvcname//" viewvc.conf
   fi

fi


exit; 

```

---

