---
title: "sed Expressions"
date: 2010-05-16
forum: Programming Talk
---

### Post by miniCruzer on 2010-05-16
I'm writing Perl scripts to generate configs for different types of daemons. I find it a pain to have to copy and paste 
```

print FILENAME "Text here\n";

```Over, and over, and over. Then, I have to go back through and add 
```

\n";

```to the end of each line.
The most painstaking part is adding a \ in front of each quote or @ symbol that appears. For example in Atheme IRC Services config, there are hundreds of lines that look like this:
```
 loadmodule "modules/chanserv/quiet"
```that need to look like
```
 print ATHEMECONF "loadmodule \"modules/chanserv/quiet\\n";
```I was thinking I could use sed to do this swiftly
```
sed -i 's/^/print ATHEMECONF "/g;s/$/\n/g' atheme.conf
```worked great, but I still have lots of work to do.

---

### Post by gmargo on 2010-05-17
There are many ways to get where you want to go without that type of editing.

Perl is a programming language.  Make it work for you.  One obvious solution is to write a function that massages the string as it goes out.  Another is to use a different quoting mechanism.

One example, for your IRC config, using a different quoting mechanism allows you to skip escaping quotes and @ symbols.  And stored like this, the newlines don't have to be added; they're already there.
```

my $athmconfig = q(
loadmodule "modules/chanserv/quiet"
loadmodule "modules/chanserv/noisy"
loadmodule "modules/chanserv/left"
loadmodule "modules/chanserv/right"
);
print ATHEMECONF $athmconfig;

```Here's a function to add newlines if needed.
```

sub prnl
{
    my ($fh, $lines) = @_;
    print $fh $lines;
    print $fh "\n" unless $lines =~ /\n\z/s;
}
prnl(*ATHEMECONF, "Text here without newline");
prnl(*ATHEMECONF, "Text here with newline\n");
prnl(*ATHEMECONF, qq(Text with "quote" and @ characters, isn't it nice?));

```

Two types of quoting mechanism shown above: 
q() - acts like single quotes (no interpolation for variables)
qq() - acts like double quotes (will interpret $variables)

---

### Post by miniCruzer on 2010-05-18
Many thanks to you. That did the trick and makes my life so much easier.

---

