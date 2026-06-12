---
title: "Problems configuring gitweb"
date: 2010-07-22
forum: Programming Talk
---

### Post by ju2wheels on 2010-07-22
Hi guys, have any of you successfully installed gitweb on 10.04 before? Ive been at this for about a day and a half now and its truly driving me bonkers. Ive been able to configure gitolite to work perfectly, I can push/pull/create repos and manage different users, but gitweb is another beast in its own right.

To provide a basis, I have an unmodified apache install and an unmodified gitweb install. Besides making sure i had cgi and rewrite modules enabled I have not made any other changes to the apache confs.

Note that my git repo root /home/user/repositories and gitolite root is /home/user.

/etc/gitweb.conf:
```


# path to git projects (<project>.git)
#$projectroot = "/var/cache/git";

$GIT = "/usr/bin/git";
$site_name= "MY GIT";
$export_ok= "git-daemon-export-ok";

$feature{'pathinfo'}{'default'} = [1];

$feature{'blame'}{'default'} = [1];
$feature{'blame'}{'override'} = [1];

$feature{'pickaxe'}{'default'} = [1];
$feature{'pickaxe'}{'override'} = [1];

$feature{'snapshot'}{'default'} = [1];
$feature{'snapshot'}{'override'} = [1];

$feature{'search'}{'default'} = [1];

$feature{'grep'}{'default'} = [1];
$feature{'grep'}{'override'} = [1];

# directory to use for temp files
$git_temp = "/tmp";

# target of the home link on top of all pages
#$home_link = $my_uri || "/";

# html text to include at home page
$home_text = "indextext.html";

# file with project list; by default, simply scan the projectroot dir.
#$projects_list = $projectroot;

# stylesheet to use
$stylesheet = "/gitweb/gitweb.css";

# javascript code for gitweb
$javascript = "/gitweb/gitweb.js";

# logo to use
$logo = "/gitweb/git-logo.png";

# the 'favicon'
$favicon = "/gitweb/git-favicon.png";

#Included from gitolite:

# --------------------------------------------
# Per-repo authorization based on gitolite ACL
# Include this in gitweb.conf
# See doc/3-faq-tips-etc.mkd for more info

# HOME of the gitolite user
my $gl_home = "/home/MYUSER";

# environment variables needed by gitolite.pm
$ENV{GL_RC} = "$gl_home/.gitolite.rc";
$ENV{GL_USER} = $cgi->remote_user || "gitweb";

# variables from the RC file
our ($REPO_BASE, $GL_ADMINDIR);

# set HOME temporarily for RC parsing
my $orig_home = $ENV{HOME};
$ENV{HOME} = $gl_home;
do $ENV{GL_RC}
    or die_error(500, "Failed to parse $ENV{GL_RC}: "  . ($! or $@));
$ENV{HOME} = $orig_home;

# set project root etc. absolute paths
$ENV{GL_REPO_BASE_ABS} = ( $REPO_BASE =~ m(^/) ? $REPO_BASE : "$gl_home/$REPO_BASE" );
$projects_list = $projectroot = $ENV{GL_REPO_BASE_ABS};

# load gitolite helper routines
require "$GL_ADMINDIR/src/gitolite.pm"
    or die_error(500, "Failed to parse gitolite.pm: " . ($! or $@));

$export_auth_hook = sub {
    my $repo = shift;
    # gitweb passes us the full repo path; so we strip the beginning
    # and the end, to get the repo name as it is specified in gitolite conf
    return unless $repo =~ s/^\Q$projectroot\E\/?(.+)\.git$/$1/;

    # check for (at least) "R" permission
    my ($perm, $creator) = &repo_rights($repo);
    return ($perm =~ /R/);

```

/home/MYUSER/.gitolite.rc :
```


# paths and configuration variables for gitolite

# please read comments before editing

# this file is meant to be pulled into a perl program using "do" or "require".

# You do NOT need to know perl to edit the paths; it should be fairly
# self-explanatory and easy to maintain perl syntax :-)

# --------------------------------------
# Do not uncomment these values unless you know what you're doing
$GL_PACKAGE_CONF = '/usr/local/share/gitolite/conf';
$GL_PACKAGE_HOOKS = '/usr/local/share/gitolite/';

# --------------------------------------

# --------------------------------------

# this is where the repos go.  If you provide a relative path (not starting
# with "/"), it's relative to your $HOME.  You may want to put in something
# like "/bigdisk" or whatever if your $HOME is too small for the repos, for
# example

$REPO_BASE="repositories";

# the default umask for repositories is 0077; change this if you run stuff
# like gitweb and find it can't read the repos.  Please note the syntax;  the
# leading 0 is required

#$REPO_UMASK = 0077;         # gets you 'rwx------'
# $REPO_UMASK = 0027;       # gets you 'rwxr-x---'
 $REPO_UMASK = 0022;       # gets you 'rwxr-xr-x'

# part of the setup of gitweb is a variable called $projects_list (please see
# gitweb documentation for more on this).  Set this to the same value:

$PROJECTS_LIST = $ENV{HOME} . "/projects.list";

# --------------------------------------

# I see no reason anyone may want to change the gitolite admin directory, but
# feel free to do so.  However, please note that it *must* be an *absolute*
# path (i.e., starting with a "/" character)

# gitolite admin directory, files, etc

$GL_ADMINDIR=$ENV{HOME} . "/.gitolite";

# --------------------------------------

# templates for location of the log files and format of their names

# I prefer this template (note the %y and %m placeholders)
# it produces files like `~/.gitolite/logs/gitolite-2009-09.log`

$GL_LOGT="$GL_ADMINDIR/logs/gitolite-%y-%m.log";

# other choices are below, or you can make your own -- but PLEASE MAKE SURE
# the directory exists and is writable; gitolite won't do that for you (unless
# it is the default, which is "$GL_ADMINDIR/logs")

# $GL_LOGT="$GL_ADMINDIR/logs/gitolite-%y-%m-%d.log";
# $GL_LOGT="$GL_ADMINDIR/logs/gitolite-%y.log";

# --------------------------------------

# Please DO NOT change these three paths

$GL_CONF="$GL_ADMINDIR/conf/gitolite.conf";
$GL_KEYDIR="$GL_ADMINDIR/keydir";
$GL_CONF_COMPILED="$GL_ADMINDIR/conf/gitolite.conf-compiled.pm";

# --------------------------------------

# if git on your server is on a standard path (that is
#       ssh git@server git --version
# works), leave this setting as is.  Otherwise, choose one of the
# alternatives, or write your own

$GIT_PATH="";
# $GIT_PATH="/opt/bin/";

# --------------------------------------

# ----------------------------------------------------------------------
#                   BIG CONFIG SETTINGS

# Please read doc/big-config.mkd for details

$GL_BIG_CONFIG = 0;
$GL_NO_DAEMON_NO_GITWEB = 0;

# ----------------------------------------------------------------------
#                   SECURITY SENSITIVE SETTINGS
#
#       Settings below this point may have security implications.  That
#       usually means that I have not thought hard enough about all the
#       possible ways to crack security if these settings are enabled.

#       Please see details on each setting for specifics, if any.
# ----------------------------------------------------------------------



# --------------------------------------
# ALLOW REPO ADMIN TO SET GITCONFIG KEYS
#
# Gitolite allows you to set git repo options using the "config" keyword; see
# conf/example.conf for details and syntax.
#
# However, if you are in an installation where the repo admin does not (and
# should not) have shell access to the server, then allowing him to set
# arbitrary repo config options *may* be a security risk -- some config
# settings may allow executing arbitrary commands.
#
# You have 3 choices.  By default $GL_GITCONFIG_KEYS is left empty, which
# completely disables this feature (meaning you cannot set git configs from
# the repo config).

$GL_GITCONFIG_KEYS = "";

# The second choice is to give it a space separated list of settings you
# consider safe.  (These are actually treated as a set of regular expression
# patterns, and any one of them must match).  For example:
# $GL_GITCONFIG_KEYS = "core\.logAllRefUpdates core\..*compression";
# allows repo admins to set one of those 3 config keys (yes, that second
# pattern matches two settings from "man git-config", if you look)
#
# The third choice (which you may have guessed already if you're familiar with
# regular expressions) is to allow anything and everything:
# $GL_GITCONFIG_KEYS = ".*";

# --------------------------------------
# EXTERNAL COMMAND HELPER -- HTPASSWD

# security note: runs an external command (htpasswd) with specific arguments,
# including a user-chosen "password".

# if you want to enable the "htpasswd" command, give this the absolute path to
# whatever file apache (etc) expect to find the passwords in.

$HTPASSWD_FILE = "";

# Look in doc/3 ("easier to link gitweb authorisation with gitolite" section)
# for more details on using this feature.

# --------------------------------------
# EXTERNAL COMMAND HELPER -- RSYNC

# security note: runs an external command (rsync) with specific arguments, all
# presumably filled in correctly by the client-side rsync.

# base path of all the files that are accessible via rsync.  Must be an
# absolute path.  Leave it undefined or set to the empty string to disable the
# rsync helper.

$RSYNC_BASE = "";

# $RSYNC_BASE = "/home/git/up-down";
# $RSYNC_BASE = "/tmp/up-down";

# --------------------------------------
# EXTERNAL COMMAND HELPER -- SVNSERVE

# security note: runs an external command (svnserve) with specific arguments,
# as specified below. %u is substituted with the username.

# This setting allows launching svnserve when requested by the ssh client.
# This allows using the same SSH setup (hostname/username/public key) for both
# SVN and git access. Leave it undefined or set to the empty string to disable
# svnserve access.

$SVNSERVE = "";
# $SVNSERVE = "/usr/bin/svnserve -r /var/svn/ -t --tunnel-user=%u";

# --------------------------------------
# ALLOW REPO CONFIG TO USE WILDCARDS

# security note: this used to in a separate "wildrepos" branch.  You can
# create repositories based on wild cards, give "ownership" to the specific
# user who created it, allow him/her to hand out R and RW permissions to other
# users to collaborate, etc.  This is powerful stuff, and I've made it as
# secure as I can, but it hasn't had the kind of rigorous line-by-line
# analysis that the old "master" branch had.

# This has now been rolled into master, with all the functionality gated by
# this variable.  Set this to 1 if you want to enable the wildrepos features.
# Please see doc/4-wildcard-repositories.mkd for details.

$GL_WILDREPOS = 1;

# --------------------------------------
# DEFAULT WILDCARD PERMISSIONS

# If set, this value will be used as the default user-level permission rule of
# new wildcard repositories. The user can change this value with the setperms command
# as desired after repository creation; it is only a default. Note that @all can be
# used here but is special; no other groups can be used in user-level permissions.

# $GL_WILDREPOS_DEFPERMS = 'R = @all';

# --------------------------------------
# HOOK CHAINING

# by default, the update hook in every repo chains to "update.secondary".
# Similarly, the post-update hook in the admin repo chains to
# "post-update.secondary".  If you're fine with the defaults, there's no need
# to do anything here.  However, if you want to use different names or paths,
# change these variables

# $UPDATE_CHAINS_TO = "hooks/update.secondary";
# $ADMIN_POST_UPDATE_CHAINS_TO = "hooks/post-update.secondary";

# --------------------------------------
# ADMIN DEFINED COMMANDS

# WARNING: Use this feature only if (a) you really really know what you're
# doing or (b) you really don't care too much about security.  Please read
# doc/admin-defined-commands.mkd for details.

$GL_ADC_PATH = "$GL_ADMINDIR/adc";

# --------------------------------------
# per perl rules, this should be the last line in such a file:
1;

# Local variables:
# mode: perl
# End:
# vim: set syn=perl:

```

gitolite-admin/conf/gitolite.conf:
```

	repo	Utilities/.+
		C	=   MYUSER
		RW+CD	=   CREATOR

        repo    gitolite-admin
		R       =   gitweb
                RW+     =   MYUSER

	gitolite-admin "MYUSER" = "Gitolite administration repo"

        repo    testing
		R       =   gitweb
                RW+CD   =   @all

	testing "MYUSER" = "Testing repository"

```

At the moment I can access the main gitweb page through [http://localhost/gitweb/](http://localhost/gitweb/), however I get a 404 No projects found message in the center.

If anyone could provide some direction it would greatly be appreciated, thanks.

Note: I replaced my usser name above with "user" or "MYUSER" purposely, but its correct on my end with the same user.

---

### Post by benoit.caccinolo on 2010-08-25
I hope it can help, I did a post about the way I configured gitweb

[http://ruready.tumblr.com/post/1008951976/gitweb-configuration-easy-way](http://ruready.tumblr.com/post/1008951976/gitweb-configuration-easy-way)

---

### Post by nrub on 2011-03-25
I'm running into a similar if not the same issue.

Debugging gitweb.cgi a bit makes me believe it's a permissions error on my projects.list file, but the permissions should be correct. Gitweb was working on this server earlier.

Gitweb is failing where we check if projects.list is a file:
```

        if (-d $projects_list) {
                ...
        } elsif (-f $projects_list) {
                # read from file(url-encoded):                                                                                                    
                # 'git%2Fgit.git Linus+Torvalds'                                                                                                  
                # 'libs%2Fklibc%2Fklibc.git H.+Peter+Anvin'                                                                                       
                # 'linux%2Fhotplug%2Fudev.git Greg+Kroah-Hartman'                                                                                 
                my %paths;
                open my $fd, '<', $projects_list or return;

                ...
        }

```

The permissions on my projects.list file are:
```

-rw-r--r--  1 gitolite gitolite  284 2011-03-25 11:20 projects.list

```

Anyone have any further insight?

---

### Post by nrub on 2011-03-25
FIgured it out. It was the parent directory not the file causing the problems.

Solution:
```

chmod a+x /var/lib/gitolite/

```

---

