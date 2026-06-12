---
title: "Program Launcher Needs Help"
date: 2008-10-17
forum: Programming Talk
---

### Post by Paul Lonon on 2008-10-17
I can not get this code worked out can anyone help. Mainly the Log::Log4perl 
[PHP]
#!/usr/local/bin/perl -w

use strict;
use Log::Log4perl qw(:easy);
use DB_File;
use Tk;

my %sudo_programs = map { $_ => 1 } 
                    qw(synaptic);

my @misc_paths = qw(/usr/sbin);

my($home) = glob "~";
my $paulyprog_dir = "$home/.paulyprog";

#Log::Log4perl->easy_init();

if(! -d $paulyprog_dir) {
  mkdir $paulyprog_dir, 0755 or
    LOGDIE "Cannot mkdir $paulyprog_dir ($!)";
}

  # Init database
my %DB_FILE;
tie %DB_FILE, 
    "DB_File", "$paulyprog_dir/db_file.dat" 
        or LOGDIE "$!";

  # Application window
my $top = MainWindow->new();
$top->geometry("-0+0");

my($input, $first_match, $label_text);

my $label = $top->Label(
  -textvariable => \$label_text, 
  -width        => 20 );

my $entry = $top->Entry( 
  -textvariable    => \$input, 
  -validatecommand => \&validate,
  -validate        => "key",
);

$entry->pack( -side => "left" );
$label->pack( -side => "left" );

$entry->bind("<Control-Key-q>", \&bail);
$entry->bind("<Return>", 
             sub { launch($input) });
$entry->bind("<Tab>", \&complete);

$entry->focus();
MainLoop;

###########################################
sub bail {
###########################################

  $top->destroy();
}

###########################################
sub validate {
###########################################
  my($got) = @_;
  $label_text = join "\n", matches($got);
  return 1;
}

###########################################
sub matches {
###########################################
  my($got) = @_;

  my @all = sort keys %DB_FILE;
  my @matches = grep { /^$got/ } @all;
  if(@matches) {
      $first_match = $matches[0];
  } else {
      $first_match = undef;
  }
  return @matches;
}

###########################################
sub complete {
###########################################

  $input = $first_match;
  launch($input);
}

###########################################
sub launch {
###########################################
  my($program) = @_;

  my $path = path_search( $program );

  LOGDIE "$program not found ",
         "in path ($ENV{PATH})" unless
             defined $path;

  $DB_FILE{ $program }++ if defined $path;
  DEBUG "Launching $path";
  untie %DB_FILE;
  if(exists $sudo_programs{ $program } ) {
      exec "xterm", "-e", "sudo", "$path";
  } else {
      exec $path;
  }
  LOGDIE "exec $path failed: $!";
}

###########################################
sub path_search {
###########################################
  my($program) = @_;

  DEBUG "PATH is $ENV{PATH}";

  for my $path ( split(/:/, $ENV{PATH}), 
                 @misc_paths ) {
      if(-x "$path/$program") {
          DEBUG "$program found in $path";
          return "$path/$program";
      }
  }

  ERROR "$program not found";
  return undef;
}
[/PHP]

---

### Post by LaRoza on 2008-10-17
Perl is hard enough to read by itself. Please use the proper tags for posting it so people will read it.

[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

---

