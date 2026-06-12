---
title: "can anyone explain the command for me:)"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by warmsuns on 2013-03-06
spell -x +ADDED_WORDS_LIST word_tmp_sort > word_tmp_spell

I really want to know that should the file"ADDED_WORDS_LIST" exist already and has contents inside ,as I can't find a file with this name in my system. the command is a part of a sentence 
in a program:)
Thanks a lot!

---

### Post by dawidnor on 2013-03-06
Take a look at this [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by drmrgd on 2013-03-06
It'll be a bit hard to figure this out without the rest of the script.  As far as I know 'spell' is not a standard Linux command, and I'm guessing it's either a function or other script that's being called by the script you're looking at.  I'm guessing it's probably another script that takes a couple arguments based on the '-x ADDED_WORDS_LIST' bit.  Maybe add the whole script (please use the CODE tags so it's readable), and we'll have a better idea.

---

### Post by r-senior on 2013-03-06
The -x option is ignored by GNU spell so that does nothing on a GNU/Linux system. The other parameters are filenames containing text to be spell-checked. These are not standard system files. The one with the '+' at the start does look odd but '+' is valid as the first character of a filename. 

So this command says, "Check the files '+ADDED_WORDS_LIST' and 'word_tmp_sort' and list any words that are not in the standard dictionary. Put the output into a file called 'word_tmp_spell'".

---

### Post by warmsuns on 2013-03-07
[SIZE=3]```
#!/site/bin/perl

open(IN,"$ARGV[0]");
open(OUT1, "> $ARGV[0]_words");
open(OUT2, "> words_in_$ARGV[0]");
while (<IN>) {
    $sentence = $_;
    print OUT1 "$sentence";
    print " sentence: $sentence";
    @words = split /\W/ , $sentence;
    open(TMP,"> word_tmp");
    foreach $word (@words) {
    $word =~ tr/[A-Z]/[a-z]/;
        print "     word $word \n";
        print TMP "$word\n";
    }
    close(TMP);
    system("sort -o word_tmp_sort word_tmp");
    system("spell -x +$ARGV[1] word_tmp_sort > word_tmp_spell");
    system("uniq word_tmp_spell > word_uniq");
    open(TMP1,"word_uniq");
    while (<TMP1>) {
    $_ =~ s/=//;
    print OUT1 "$_";
    print OUT2 "$_";
        print "$_";
    }
    close(TMP1);
    unlink(word_tmp_lower);
   unlink(word_tmp_spell);
    unlink(word_tmp);
    unlink(word_tmp_sort);
   unlink(word_uniq);
    print OUT1 "===\n";
}
close(IN);
close(OUT1);
close(OUT2);


```


in fact , what I ask about is from a perl code with the name of 'sentence_words'([SIZE=3]a[SIZE=3]bove i[SIZE=3]s the co[SIZE=3]de)[/SIZE][/SIZE][/SIZE][/SIZE],[SIZE=3] [/SIZE][COLOR=#ff0000]system("spell -x +$ARGV[1] word_tmp_sort > word_tmp_spell")[/COLOR][SIZE=3] [/SIZE]is a senten[SIZE=3]ce among [SIZE=3]a[SIZE=3]bove.[/SIZE][/SIZE][/SIZE]
and the perl program which calls 'sentence_words' uses the following sentence to do that: system("perl sentence_words [COLOR=#ff0000]SENTENCES ADDED_WORDS_LIST[/COLOR]"); I can find SENTENCES ,now  ADDED_WORDS_LIST has also been found.

[SIZE=4]So now the command can be translated into : spell  -x +ADDED_WORDS_LIST word_tmp_sort > word_tmp_spell
which means : words from 'word_tmp_sort' which are  not literally in the spelling list are stored in file 'word_tmp_spell',and words present in ADDED_WORDS_LIST are removed from the output as additional correctly spelled words.[/SIZE]

but the system can not recongnize "+ADDED_WORDS_LIST", maybe it is because the code was written in a very old version of linux.

C[SIZE=3]an someone tell me what I should do to re[SIZE=3]alize the same function or the m[SIZE=3]ake it work under my system. Thanks so[SIZE=3] so much:)[/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]

---

### Post by warmsuns on 2013-03-07
the link is very useful ,thanks :)

---

### Post by schragge on 2013-03-07
It's an old spell syntax from legacy versions of Unix: you can look it up in the [SUSv2]("http://pubs.opengroup.org/onlinepubs/007908799/xcu/spell.html") or at the [Heirloom Toolchest project]("http://heirloom.sourceforge.net/man/spell.1.html").

---

### Post by warmsuns on 2013-03-08
> **schragge said:**
> It's an old spell syntax from legacy versions of Unix: you can look it up in the [SUSv2]("http://pubs.opengroup.org/onlinepubs/007908799/xcu/spell.html") or at the [Heirloom Toolchest project]("http://heirloom.sourceforge.net/man/spell.1.html").
Thank you so much:) I will look into them:) Could please tell me since it is an old syntax ,How can I make the commnd work in my own system?

---

### Post by warmsuns on 2013-03-08
> **schragge said:**
> It's an old spell syntax from legacy versions of Unix: you can look it up in the [SUSv2]("http://pubs.opengroup.org/onlinepubs/007908799/xcu/spell.html") or at the [Heirloom Toolchest project]("http://heirloom.sourceforge.net/man/spell.1.html").

Since it is an old version. Could you give me some idea how to make it work for my system now?

---

### Post by schragge on 2013-03-08
[Here]("http://manpages.ubuntu.com/manpages/precise/en/man1/spell.1.html") is the manual page of spell in Ubuntu. Compare for youself. There are also other spell-checking command line tools like [aspell]("http://manpages.ubuntu.com/manpages/precise/en/man1/aspell.1.html") and [hunspell]("http://manpages.ubuntu.com/manpages/precise/en/man1/hunspell.1.html").

---

