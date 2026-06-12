---
title: "Fixing Japanese Fonts in Dapper"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by kairu0 on 2006-06-27
This is a short method for improving the default fonts for a much more readible set. I'm not a font expert, but hopefully someone will find this useful.

1. Add the ubuntu-ja repositories in a terminal:

```

sudo gedit /etc/apt/sources.list

```

Add to the bottom:

```

deb http://archive.ubuntulinux.jp/ubuntu-ja dapper/
deb http://archive.ubuntulinux.jp/ubuntu-ja dapper-ja/
```

Close gedit. Type:

```
sudo apt-get update
sudo apt-get install ipafont ipamonofont
sudo mv /etc/fonts/local.conf /etc/fonts/local.conf.backup
gedit /etc/fonts/local.conf
```

Copy the following into the new file, save, and exit:

```
<fontconfig>
	<match target="font">
		<edit name="embeddedbitmap" mode="assign">
			<bool>false</bool>
		</edit>
		<edit name="autohint" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>hintnone</const>
		</edit>
	</match>

	<match target="font">
		<test name="lang" compare="contains">
			<string>ja</string>
		</test>
		<test name="spacing" compare="eq">
			<const>dual</const>
		</test>
		<edit name="spacing">
			<const>proportional</const>
		</edit>
		<edit name="globaladvance" binding="strong">
			<bool>false</bool>
		</edit>
	</match>

	<match target="font">
		<test name="lang" compare="contains">
			<string>ja</string>
		</test>
		<test name="outline" compare="eq">
			<bool>false</bool>
		</test>
		<test name="spacing" compare="eq">
			<const>mono</const>
			<const>charcell</const>
		</test>
		<edit name="spacing">
			<const>proportional</const>
		</edit>
		<edit name="globaladvance" binding="strong">
			<bool>false</bool>
		</edit>
	</match>

	<match target="pattern">
		<test qual="any" name="family">
			<string>sans-serif</string>
		</test>
		<edit name="family" mode="prepend" binding="strong">
			<string>IPAMonaPGothic</string>
			<string>IPAPGothic</string>
			<string>Sazanami Gothic</string>
			<string>Kochi Gothic</string>
		</edit>
	</match> 
	<match target="pattern">
		<test qual="any" name="family">
			<string>serif</string>
		</test>
		<edit name="family" mode="prepend" binding="strong">
			<string>IPAMonaPMincho</string>
			<string>IPAPMincho</string>
			<string>Sazanami Mincho</string>
			<string>Kochi Mincho</string>
		</edit>
	</match> 
	<match target="pattern">
		<test qual="any" name="family">
			<string>monospace</string>
		</test>
		<edit name="family" mode="prepend" binding="strong">
			<string>IPAMonaGothic</string>
			<string>IPAGothic</string>
			<string>Sazanami Gothic</string>
			<string>Kochi Gothic</string>
		</edit>
	</match> 
</fontconfig>

```

Reboot (or log out, kill gdm, and restart it.)

* This method will make your Japanese fonts look ridiculously good, but it will also change your default sans, serif, etc. system fonts' settings. In the end, it was worth it for me.

** The above local.conf was taken from [http://people.ubuntu.com/~mvo/bzr/language-selector/language-selector--mvo/fontconfig/ja_JP](http://people.ubuntu.com/~mvo/bzr/language-selector/language-selector--mvo/fontconfig/ja_JP). I take no credit for this file, unless it be monetary ;)

---

### Post by Endukugga on 2006-07-02
Hi, I wrote a HOWTO for nice Japanese font display [here]("http://ubuntuforums.org/showthread.php?t=206280").

I thought you might be interested in checking it out. Feedback is welcome!

---

