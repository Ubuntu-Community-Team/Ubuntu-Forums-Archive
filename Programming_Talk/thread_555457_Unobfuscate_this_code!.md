---
title: "Unobfuscate this code!"
date: 2007-09-20
forum: Programming Talk
---

### Post by samjh on 2007-09-20
I've just come across [www.perlmoks.org](www.perlmoks.org).  It looks like a Perl programming website, boasting many weird uses of Perl.

Since I'm not a Perl programmer, curiosity got the better of me, and upon a little shallow browsing of the site's contents, I discovered this obfuscated Perl code which happens to be the most creative use of obfuscated code I've ever seen!

Original here: [http://www.perlmonks.org/?node=Obfuscated%20Code](http://www.perlmonks.org/?node=Obfuscated%20Code)

```
                                                       my $f="^("
                                                     ;my $r = '"';my$c
                                                 = 1; my $i; my $t;sub
                                                  llama{my $n=shift;my
                                                    $r=""; for
                                                    (1..11){$r
                                                    .=($n>=(2
                                                    **(11-$_))
                                                     )?1:0;if(
                                                    rindex($r,
                                                    "1")==$_-1
                                                   ){$n-=(2**(
  11-$_));}} return $r;}$_ = "0";$_.=llama(1855) ; $_ .=llama(
188);$_.=llama(935); my   @i= split(//,$_);foreach(@i){#;+++''
$_+=2;$f.='.'x$_.')('; $r.='$'.$c++.' ';}$r .= '"';#';+++;++'
$f.=')';my $string = "";foreach(<DATA>){$string.=$_;}#'+#++;:
$string =~ s/[ \n]//g;my@g=unpack("C*",$string);#;';:;##+'#
  my $st="";for(1..44){$st .= (($t=(($i=shift(@g))==#';###':
   38)?$i+shift(@g):$i-shift(@g))<=9)?#,.+'';'';';+'''++@#,
    "0".$t:$t;}$_=$st ."4";#++'##+;',::',;;+#;+##,;;@#@#+,
    /$f/;###';##';;;;++#+@++@#+#@+'',:'';'''+##+@;#:+@#:;
    my $s = eval $r;#`'+@@@@##@@@+###@#;,''#@@+@''++#+',
     my @p = split(/ /, $s);#@@@@+#@'@'+##+##@+#@++#@,`
      print pack("C*",@p). "\n";###@#@+#;@##+@######'`
       #@@#'';:+'''+#++`    '@@@#@#@@@###@@####@#+',.
         #@@+;##;'+;+#`      ,:+####@@@+#@#+#@#+@#
          #@@#++#;+##           ..+#+''#'@@@@#;+@#
           #@@##++'''             ` ,.` #@@@@#;#;.
           __DATA__                     #@@@@@@#+'
            &$.#&!                      :+.#{<?"&
            !.$.#                       .#:*.$O&%$
           .#O$<                        $.%&!.%&;
            .#_"                        %$.   #&!
            :,O&                        O/     }-
             .$.                        #<     ..
              $}                        *<     '+
              '&;                       &=     .$
               &!                        %$     .#
```Now... just what in the universe full of electrons does *that* thing do?!
:popcorn:

---

### Post by lisati on 2007-09-20
> 
"The one-l  lama, he's a priest,
The two-l llama, he's a beast,
but I will bet a silk pajama
there's no such thing as a three-l lllama"
[INDENT][INDENT]---Ogden Nash[/INDENT][/INDENT]

(Notwithstanding the conflagration known as a "three alarmer")

---

### Post by Ramses de Norre on 2007-09-20
This is a bit more readable:
```
#!/usr/bin/env perl
my $f="^(";
my $r='"';
my $c=1;
my $i;
my $t;
sub llama
{
	my $n=shift;
	my $r="";
	for(1..11)
	{
		if($n>=(2**(11-$_)))
		{
			$r.=1;
		}
		else
		{
			$r.=0;
		}
		if(rindex($r,"1")==$_-1)
		{
			$n-=(2**(11-$_));
		}
	}
	return $r;
}

$_ = "0";
$_.=llama(1855);
$_ .=llama(188);
$_.=llama(935);
my @i=split(//,$_);

foreach(@i)
{
	$_+=2;
	$f.='.'x$_.')(';
	$r.='$'.$c++.' ';
}

$r.='"';
$f.=')';
my $string="";

foreach(<DATA>)
{
	$string.=$_;
}

my @g=unpack("C*",$string);
my $st="";

for(1..44)
{
	$i=shift(@g);
	if($i==38)
	{
		$t=$i+shift(@g);
	}
	else
	{
		$t=$i-shift(@g);
	}
	if($t<=9)
	{
		$st.="0".$t;
	}
	else
	{
		$st.=$t;
	}
}

$_=$st."4";
/$f/;
my $s=eval $r;
my @p=split(/ /, $s);
print pack("C*",@p)."\n";

__DATA__                     
&$.#&!:+.#{<?"&!.$.#.#:*.$O&%$.#O$<$.%&!.%&;.#_"%$.#&!:,O&O/}-.$.#<..$}*<'+
```

As you can see the code does mainly some string operations on the string defined below __DATA__ .

---

### Post by Keymone on 2007-09-20
[http://www.ioccc.org/](http://www.ioccc.org/)

---

### Post by LaRoza on 2007-09-20
How about this Perl program, run it and see!

[http://99-bottles-of-beer.net/language-perl-737.html](http://99-bottles-of-beer.net/language-perl-737.html)

---

### Post by pmasiar on 2007-09-20
> **samjh said:**
> Now... just what in the universe full of electrons does *that* thing do?!


... where, of course, the O'Reilly book "Programming Perl" is called "Camel book" (with picture of camel), and "Learning Perl" is "Llama book", and has picture of llama. Rumors are, camel was selected because it is like Perl: ugly, almost impossible to master, but durable and able to accomplish what no other beast can.

---

### Post by samjh on 2007-09-20
> **LaRoza said:**
> How about this Perl program, run it and see!

[http://99-bottles-of-beer.net/language-perl-737.html](http://99-bottles-of-beer.net/language-perl-737.html)

I have a deep dislike of ugly code, but I must admit that is impressive.

[QUOTE=pmasiar]O'Reilly book "Programming Perl" is called "Camel book" (with picture of camel), and "Learning Perl" is "Llama book", and has picture of llama.[/quote]Yep, I found that out while I was browsing the O'Reilly website, which is how I came to stumble across the perlmonks one.  That's why I found the obfuscation so funny. :)

---

### Post by LaRoza on 2007-09-20
[QUOTE=samjh;3396323]I have a deep dislike of ugly code, but I must admit that is impressive.
\/QUOTE]

It uses Perl RE (I believe), I don't pretend to understand it!

---

