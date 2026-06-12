---
title: "packages for emacs question (php-elisp)"
date: 2016-10-31
forum: New to Ubuntu
---

### Post by tonma on 2016-10-31
I'm new to Ubuntu in general, and I'm just trying to learn to use emacs as well;
I downloaded emacs, and created some .php files which were not indented or colored. So I searched around and found a topic (but only single topic in the entire search!) that suggested to do sudo apt-get install php-elisp.
That did work! Now my php files are colored and indented. But my question is.. Since Ubuntu is open-source, how can I tell if it's a legit package, and not some malware - there is barely any information on this php-elisp package? How do I know if it's safe to  use?

*Edit: I noticed that php-elisp actually installs "php-mode" which is in the official emacs wiki.. so how come the package name is php-elisp but it installs php-mode? confusing for beginners :)

---

### Post by Impavidus on 2016-10-31
You installed php-elisp from the official Ubuntu repositories. You can trust those. Or not, but in that case you shouldn't trust anything on your computer.

php-elisp is a debian-type package. debian-type packages (.deb files) are the type of packages used by Ubuntu's package management system. Although I'm not so familiar with emacs, I think emacs can be expanded using some sort of emacs-type packages. So php-mode is an emacs package. Debian packages may provide a singe emacs package, or a bundle of them. It works the same way with many other programs that can be expanded using packages.

---

### Post by SeijiSensei on 2016-10-31
I use [jed]("http://www.jedsoft.org"), an Emacs clone by John E. Davis at MIT that is in the standard repositories. It comes with a PHP mode by default.  I get highlight colors and indentation based on the file's extension.  Since most of my code exists outside the web tree and is included by the .php scripts in those directories, all my code is stored in files with .inc extensions.  I added a few lines of code to ~/.jedrc to apply php_mode to .inc files.

I haven't used Emacs since my  graduate school years.  Does it have menus nowadays?  If not, jed has a helpful top-line menu that gives you access to those more obscure commands whose Ctrl-key sequences you may not have memorized.

---

