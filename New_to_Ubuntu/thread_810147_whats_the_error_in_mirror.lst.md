---
title: "whats the error in mirror.lst?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-28
I get:

```

root@ubuntu:~# apt-mirror -c apt-mirror
apt-mirror: invalid config file specified at /usr/bin/apt-mirror line 101.

```

while here is the mirror.lst:

```

deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://apt.wicd.net hardy extras
deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/corenominal/ubuntu gutsy main



deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://ppa.launchpad.net/corenominal/ubuntu gutsy main


clean ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/
clean http://archive.canonical.com/
clean http://apt.wicd.net/
clean http://packages.medibuntu.org/
clean http://ppa.launchpad.net/

############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     20
set _tilde 0
#
############# end config ##############

```

101 line doesnt event exist as per my emacs statement.

---

### Post by HotShotDJ on 2008-05-28
```
apt-mirror: invalid config file specified at /usr/bin/apt-mirror line 101
```This error appears to be referring to an error in apt-mirror at line #101, not mirror.lst

---

### Post by shoaibi on 2008-05-28
how can i correct that :(
i just installed it via apt-get

---

### Post by HotShotDJ on 2008-05-28
> **shoaibi said:**
> how can i correct that :(
i just installed it via apt-getI wouldn't have any idea without seeing line 101 of /usr/bin/apt-mirror

---

### Post by shoaibi on 2008-05-28
here it is:

```

#!/usr/bin/perl -w

=pod

=head1 NAME

apt-mirror - apt sources mirroring tool

=head1 SYNOPSIS

apt-mirror [configfile]

=head1 DESCRIPTION

A small and efficient tool that lets you mirror a part of or
the whole Debian GNU/Linux distribution or any other apt sources.

Main features:
 * It uses a config similar to apts F<sources.list>
 * It's fully pool comply
 * It supports multithreaded downloading
 * It supports multiple architectures at the same time
 * It can automatically remove unneeded files
 * It works well on overloaded channel to internet
 * It never produces an inconsistent mirror including while mirroring
 * It works on all POSIX complied systems with perl and wget

=head1 COMMENTS

apt-mirror uses F</etc/apt/mirror.list> as a configuration file.
By default it is tuned to official debian mirror in Finland. Change
it for your needs.

After you setup the configuration file you may run as root:

    # su - apt-mirror -c apt-mirror

Or uncomment line in F</etc/cron.d/apt-mirror> to enable daily mirror upgrades.

=head1 FILES

F</etc/apt/mirror.list>
        Main configuration file

F</etc/cron.d/apt-mirror>
        Cron configuration template

F</var/spool/apt-mirror/mirror>
        Mirror places here

F</var/spool/apt-mirror/skel>
        Place for temporarily downloaded indexes

F</var/spool/apt-mirror/var>
        Log files placed here. URLs and MD5 summs also here.

=head1 KNOWN BUGS

Do not specify default http port (80) explicitly. (i.e. deb http://server:80/ sid ...)

=head1 AUTHOR

Dmitry N. Hramtsov E<lt>hdn@nsu.ruE<gt>

=cut

use strict;
use File::Copy;
use File::Path;
use File::Basename;

my $config_file;

my %config_variables = (
    "defaultarch" => `dpkg --print-installation-architecture 2>/dev/null` || 'i386',
    "nthreads"    => 20,
    "base_path"   => '/var/spool/apt-mirror',
    "mirror_path" => '$base_path/mirror',
    "skel_path"   => '$base_path/skel',
    "var_path"    => '$base_path/var',
    "cleanscript" => '$var_path/clean.sh',
    "_contents"   => 1,
    "_autoclean"  => 0,
    "_tilde"      => 0
);

my @config_binaries = ();
my @config_sources = ();

my @index_urls;
my @childrens = ();
my %skipclean = ();
my %clean_directory = ();


######################################################################################
## Setting up $config_file variable

$config_file = "/etc/apt/mirror.list";  # Default value
if($_ = shift) {
    die("apt-mirror: invalid config file specified") unless -f $_;
    $config_file = $_;
}

chomp $config_variables{"defaultarch"};

######################################################################################
## Common subroutines

sub round_number
{
        my $n = shift;
        my $minus = $n < 0 ? '-' : '';
        $n = abs($n);
        $n = int(($n + .05) * 10) / 10;
        $n .= '.0' unless $n =~ /\./;
        $n .= '0' if substr($n,(length($n) - 1),1) eq '.';
        chop $n if $n =~ /\.\d\d0$/;
        return "$minus$n";
}

sub format_bytes {
        my $bytes = shift;
        my $bytes_out = '0';
        my $size_name = 'bytes';
        my $KiB = 1024;
        my $MiB = 1024 * 1024;
        my $GiB = 1024 * 1024 * 1024;

        if ($bytes >= $KiB) {
                $bytes_out = $bytes / $KiB;
                $size_name = 'KiB';
                if ($bytes >= $MiB) {
                        $bytes_out = $bytes / $MiB;
                        $size_name = 'MiB';
                        if ($bytes >= $GiB) {
                                $bytes_out = $bytes / $GiB;
                                $size_name = 'GiB';
                        }
                }
        } else {
                $bytes_out = $bytes;
                $size_name = 'bytes';
        }

        $bytes_out = round_number($bytes_out);
        return "$bytes_out $size_name";
}

```

is that enough?

---

### Post by HotShotDJ on 2008-05-28
> **shoaibi said:**
> is that enough?Yep... that's enough.  If I'm reading apt-mirror correctly, you need to rename mirror.lst to mirror.list -- let me know if that does the trick.

---

