---
title: "how to find common lines in subset of multiple files"
date: 2016-07-31
forum: Programming Talk
---

### Post by zerop2 on 2016-07-31
[COLOR=#242729][FONT=Arial]if there is at least two files have common lines hope to show like this example,[/FONT][/COLOR]
[COLOR=#303336]perl a[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]pl [/COLOR][COLOR=#303336].[/COLOR][COLOR=#858C93]/*.txt

common line1 - a.txt b.txt
common line2 - a.txt c.txt d.txt[/COLOR][COLOR=#242729][FONT=Arial]i searched this script, but this script only search words, not common lines[/FONT][/COLOR]
[COLOR=#303336]perl theScript[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]pl [/COLOR][COLOR=#303336]?.[/COLOR][COLOR=#303336]dat 
[/COLOR][COLOR=#858C93]#! perl -nl[/COLOR][COLOR=#303336]

push [/COLOR][COLOR=#303336]@{[/COLOR][COLOR=#303336] $h[/COLOR][COLOR=#303336]{[/COLOR][COLOR=#303336] $_ [/COLOR][COLOR=#303336]}[/COLOR][COLOR=#303336] [/COLOR][COLOR=#303336]},[/COLOR][COLOR=#303336] $ARGV

[/COLOR][COLOR=#303336]}{[/COLOR][COLOR=#303336]

[/COLOR][COLOR=#101094]print[/COLOR][COLOR=#303336] qq[/COLOR][COLOR=#303336][[/COLOR][COLOR=#303336]$_ id [/COLOR][COLOR=#101094]in[/COLOR][COLOR=#303336] [/COLOR][COLOR=#303336]@{[/COLOR][COLOR=#303336]$h[/COLOR][COLOR=#303336]{[/COLOR][COLOR=#303336] $_ [/COLOR][COLOR=#303336]}}][/COLOR][COLOR=#303336] [/COLOR][COLOR=#101094]for[/COLOR][COLOR=#303336] keys [/COLOR][COLOR=#303336]%[/COLOR][COLOR=#303336]h[/COLOR][COLOR=#303336];[/COLOR]

---

