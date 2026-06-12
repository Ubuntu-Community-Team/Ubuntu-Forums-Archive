---
title: "chomp chomp chomp - perl"
date: 2008-02-02
forum: Programming Talk
---

### Post by frenchcr on 2008-02-02
Howdy,

I have a file with 2968 commands (on different lines and all ending with \n) in a file named "subfile".

I would like to put each of the commands in their own file (i.e. subfile0, subfile1, ... , up to subfile2967)


Heres how far ive got.....


```
#!/usr/bin/perl -W

$NumOfSim = shift(@ARGV);

chomp($me = `id -un`);
$PATH = "/home/$me/src/Tc/Scheme4";
$DIR = "$PATH/Simulation$NumOfSim";
$DIR2 = "$PATH/Simulation$NumOfSim/subfile_split";

open(FILEIN,"<$DIR/subfile") || die "Cannot open subfile\n";

@row_data = <FILEIN>;
close FILEIN;

for($j=0;$j<2968;$j++)   # jmax = number of job subs
{
	open(FILEOUT,">$DIR2/subfile$j") || die "Cannot open subfile$j \n";
  
	foreach $line(@row_data)
	{
	        chomp($line);
		$cmd = "$line ";
		print FILEOUT "$cmd \n";
	}#$line

}


```


 ...when i try to print each command to its own file, ALL the commands go to ALL the files  ??


Any ideas??

---

### Post by jss43 on 2008-02-02
In the print statement I think you need to use the filehandle of the opened output file, rather than a filename.

```

print FILEOUT "$cmd \n";

```

---

### Post by frenchcr on 2008-02-02
Thanks jss43. Ive corrected the original post.

I still need to make individual commands go to their own files....ALL commands are going to ALL files at the moment ??

---

### Post by frenchcr on 2008-02-02
bump

---

### Post by Tuna-Fish on 2008-02-02
> **frenchcr said:**
> 
```
#!/usr/bin/perl -W

$NumOfSim = shift(@ARGV);

chomp($me = `id -un`);
$PATH = "/home/$me/src/Tc/Scheme4";
$DIR = "$PATH/Simulation$NumOfSim";
$DIR2 = "$PATH/Simulation$NumOfSim/subfile_split";

open(FILEIN,"<$DIR/subfile") || die "Cannot open subfile\n";

@row_data = <FILEIN>;
close FILEIN;

for($j=0;$j<2968;$j++)   # jmax = number of job subs
{
	open(FILEOUT,">$DIR2/subfile$j") || die "Cannot open subfile$j \n";
  
	foreach $line(@row_data)
	{
	        chomp($line);
		$cmd = "$line ";
		print FILEOUT "$cmd \n";
	}#$line

}


```


 ...when i try to print each command to its own file, ALL the commands go to ALL the files  ??


But that's exactly what you tell it to do.

think about it. The outer for creates the files, the inner foreach is processed fully by each of the files. That's what happens when you nest control structures.

one way to do it properly:
[php]
$j = 0;
foreach $line(@row_data)
{
    open(FILEOUT,">$DIR2/subfile$j") || die "Cannot open subfile$j \n";
    $j++;
    chomp($line);
    $cmd = "$line ";
    print FILEOUT "$cmd \n";

}
[/php]

(I don't know perl, so that might be horribly wrong.)

---

### Post by frenchcr on 2008-02-02
Tuna Fish, thank you my friend. Your method works in Perl too. All the best to you.

---

