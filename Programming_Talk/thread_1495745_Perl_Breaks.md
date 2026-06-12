---
title: "Perl: Breaks"
date: 2010-05-28
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-05-28
What's Up?

OK, So my first Perl script in nearing completion, However there is still one last problem, Part of the script uploads the given file to your ftp host, But Perl breaks if i cannot find the given file, How could I get my script to carry on even if it hasn't found the file?

The appropriate part of the script. 

```
else
{
my $ftp;
my $upload ='File.tar.gz';
my $host ='ftp.ubuntu.org';
my $user ='ftp.007ubuntu.org';
my $pw   ='ubuntuforums.org';
my $path ='Files/';
chomp($host,$user,$pw,$path, $upload);
$ftp=Net::FTP->new($host) or die "could not login";
$ftp->login($user,$pw) or die "could not login";
$ftp->cwd($path) or die "could not cwd $path";
$ftp->ls;
$ftp->put($upload) or die "could not put $upload";
$ftp->site("chmod 600 " . basename($upload));
$uploadcheck = $upload;
}
```

If the file isn't there. it gives you the ' 'Cannot open Local file tar.gz.tar.gz: No such file or directory' ' message.

Anyone know?

See Ya!

*** Is the solution removing the "or die" functions after the ftp commands?

---

### Post by shawnhcorey on 2010-05-28
You do not have that error message in the code you posted.

You could change `die` to `warn`.  See `[perldoc -f warn]("http://perldoc.perl.org/functions/warn.html")`.

---

### Post by myrtle1908 on 2010-05-28
You can also check if the file exists eg

```
if (-e $upload) {
  # exists
} else {
  # no exist
}
```
 
If you are in a loop you could simply say

```
next if !-e $upload;
```

or

```
next unless -e $upload;
```

---

