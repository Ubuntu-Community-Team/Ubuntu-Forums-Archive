---
title: "Rewrite Kernel Contents"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by rayquaza on 2013-05-10
[COLOR=#000000][FONT=arial]Hey guys :)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]so I'm trying somthin out......[/FONT][/COLOR]


[COLOR=#000000][FONT=arial]rootdev -s[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]    /dev/sda5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]dd if=/dev/sda4 of=kernel_2.blob[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]dump_kernel_config kernel_2.blob > kernel_2.cfg[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]cp kernel_2.cfg kernel_debug.cfg[/FONT][/COLOR]


[COLOR=#000000][FONT=arial]Now, replace the contents of kernel_debug.cfg with the following:[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]CODE: SELECT ALL[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]add_efi_memmap [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]boot=local [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]console=tty1 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]disablevmx=off [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]i915.modeset=1 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]init=/sbin/init [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]kern_guid=%U [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]loglevel=7 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]lsm.module_locking=0 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]ro [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]root=PARTUUID=%U/PARTNROFF=1 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]rootwait [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tpm_tis.force=1 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]tpm_tis.interrupts=0[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]Essentially how do I replace the "CONTENTS OF THE KERNEL_DEBUG.CFG" do I use Bash >>>>>> OR is their some other way.......[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-05-10
I don't understand the question.  You can use* vi, vim, nano* to manually edit the file.  You can use *gedit* to use a graphical text editor.

Otherwise you have to use *gawk, sed, perl*, or some other pattern scanning and processing language to replace the key values.

A simple way would be to simply append the old file with the change file using *cat* or *tee* because the last-defined values are what is used for compilation.  I have not compiled a kernel with such a config file but it should work.

---

