---
title: "Perl and Expect help needed."
date: 2006-07-11
forum: Programming Talk
---

### Post by cancer22 on 2006-07-11
I have been running Ubuntu for a while now, and am starting to 
migrate off of some other linux distros.

I need to have Perl and Expect working to migrate off.

I have tried to install the expect module for perl, but I am getting errors when running my script trying to use expect.

Can't locate loadable object for module IO::Tty in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/IO/Tty.pm line 29

In the Tty.pm file, line 29 shows:

BOOT_XS: {
    # If I inherit DynaLoader then I inherit AutoLoader and I DON'T WANT TO
    require DynaLoader;

    # DynaLoader calls dl_load_flags as a static method.
    *dl_load_flags = DynaLoader->can('dl_load_flags');

    do {   [COLOR="Red"]----LINE 29[/COLOR]
        defined(&bootstrap)
                ? \&bootstrap
                : \&DynaLoader::bootstrap
    }->(__PACKAGE__);
}

When I try to find the DynaLoader package I see it in:
/usr/lib/perl/5.8.7/auto/DynaLoader
/usr/lib/perl/5.8.7/auto/DynaLoader/dl_find_symbol_anywhere.al
/usr/lib/perl/5.8.7/auto/DynaLoader/dl_expandspec.al
/usr/lib/perl/5.8.7/auto/DynaLoader/extralibs.ld
/usr/lib/perl/5.8.7/auto/DynaLoader/autosplit.ix
/usr/lib/perl/5.8.7/auto/DynaLoader/DynaLoader.a
/usr/lib/perl/5.8.7/auto/DynaLoader/dl_findfile.al
/usr/lib/perl/5.8.7/DynaLoader.pm


I'm not sure where or how to proceed with this problem.

Any help is appreciated.

---

### Post by cancer22 on 2006-07-11
Figured it out.... I needed to have the development tools installed, including cc and others.

---

