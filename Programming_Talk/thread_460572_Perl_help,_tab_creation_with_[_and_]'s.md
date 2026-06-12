---
title: "Perl help, tab creation with [ and ]'s"
date: 2007-05-31
forum: Programming Talk
---

### Post by xOrphenochx on 2007-05-31
I know nothing about Perl, but I'm helping a friend with his video jukebox for a convention. I fixed the rest of the script to not clean up [xxxxxx] filenames, but I need help making it create a tab for a certain phrase; [AMV]. Right now it doesn't clean that from the name in the script, but it places it in the 0-9 tab as noted in the code, already tried simpley adding AMV or [AMV] and that was a no go. If anyone knows how to fix this script, him and I would be much appreciative.

```

my $tab;
my $tabnumber=0;
foreach $tab ('0-9','A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z') {
 my $tabchar = lc($tab);

 if(exists($video->{byfirst}->{$tabchar})) {

  # Generate scrollable window for the listbox.
  my $scrollwin = Gtk2::ScrolledWindow->new;
  $widgets->{notebook}->{scrollwin}->{$tabnumber}=$scrollwin;
 
  $scrollwin->set_shadow_type ('etched-in');
 
  my $filelist = Gtk2::SimpleList->new (
 			'Filename'	=> 'text',
			'Length'	=> 'text',
			'Times Played'	=> 'int',
			'File'		=> 'file' );

  $widgets->{notebook}->{filelist}->{$tabnumber}=$filelist;
 
  $filelist->get_selection()->set_mode('single');
 
  my $file;
  my $selection=0;
  for $file (sort(keys(%{$video->{byfirst}->{$tabchar}}))) {
   my $cleanname=$video->{byfirst}->{$tabchar}->{$file};
   my $tally=&videotally($file);
   my $duration=&duration2str(&videoduration($file));
   $video->{tab}->{$file}=$tabnumber;
   $video->{selection}->{$tabnumber}->{$file}=$selection++;
   push(@{$filelist->{data}}, [ $cleanname, $duration, $tally, $file ] );
  }

```

---

### Post by xadder on 2007-06-01
Sorry, I don't understand OO perl or your problem really, but I just noticed that you use a very long way of
specifying the alphabet. try this style:

foreach $t ( '0-9', 'A' .. 'Z' ){
    print "Hi $t \n";
}

perl will figure out what's between 'A' and 'Z'.  But as I said, this won't make the code work!

---

### Post by tr333 on 2007-06-02
instead of getting a list of 'A'-'Z' and using the "lc" command to convert to lowercase, why not just get a list of lowercase characters to start with?

```

foreach $tabchar ('0-9','a'..'z') {
    # do stuff
}

```

---

### Post by xOrphenochx on 2007-06-02
I appreciate the effort, but all I need is a new tab for something that isn't only identified by the first character. I didn't write this code, and I know nothing about Perl, and the person who did isn't around anymore.

---

