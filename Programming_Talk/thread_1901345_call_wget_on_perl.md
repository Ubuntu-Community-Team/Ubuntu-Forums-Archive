---
title: "call wget on perl"
date: 2011-12-28
forum: Programming Talk
---

### Post by trotos on 2011-12-28
I'm writting a script in perl where I'm calling wget to download some files from an ftp server the command is as follows:

```
system ("wget", "--follow-ftp", "--ignore-case", "-A *chipseq*peak*.gz", "-r", "-c", "-nd", "-nH", "-P ~/Desktop/BioProject", "ftp://hgdownload.cse.ucsc.edu/goldenPath/hg18/encodeDCC/");
```

the proble is the "-P ~/Desktop/BioProject" it doesn't write anything to the Desktop but rather in the wget folder!!!

I'm on mac Os X and I've installed the wget from souce.

---

### Post by shawnhcorey on 2011-12-28
You have to expand it using glob():
```
my $dest = glob( '~/Desktop/BioProject' );
system ("wget", "--follow-ftp", "--ignore-case", "-A *chipseq*peak*.gz", "-r", "-c", "-nd", "-nH", "-P $dest", "ftp://hgdownload.cse.ucsc.edu/goldenPath/hg18/encodeDCC/");
```

---

### Post by ofnuts on 2011-12-29
> **trotos said:**
> I'm writting a script in perl where I'm calling wget to download some files from an ftp server the command is as follows:

```
system ("wget", "--follow-ftp", "--ignore-case", "-A *chipseq*peak*.gz", "-r", "-c", "-nd", "-nH", "-P ~/Desktop/BioProject", "ftp://hgdownload.cse.ucsc.edu/goldenPath/hg18/encodeDCC/");
```the proble is the "-P ~/Desktop/BioProject" it doesn't write anything to the Desktop but rather in the wget folder!!!

I'm on mac Os X and I've installed the wget from souce.The "~/" shortcut is really a shell thing, and it is not understood by the file system (the shell expands it before passing to commands). It has to be resolved (as in the post above).

---

### Post by nvteighen on 2011-12-29
Isn't there a cURL module for Perl? If there is one and I'm sure there has to be one, I think that'd be much better than calling wget like that...

---

