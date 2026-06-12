---
title: "How do I create and install a Perl module?"
date: 2010-01-21
forum: Programming Talk
---

### Post by Puzzled Guy on 2010-01-21
Hi

I used this command to create the skeleton of the module:
```
xxxx@xxxx-Laptop:~/Desktop$ h2xs -X -n TYPStats
```
And I know I am supposed to write the module itself now, but I don't know how to do it.

There is this file in the created folder, which is going to be the module:
```
package TYPStats;

use 5.010000;
use strict;
use warnings;

require Exporter;
use AutoLoader qw(AUTOLOAD);

our @ISA = qw(Exporter);

# Items to export into callers namespace by default. Note: do not export
# names by default without a very good reason. Use EXPORT_OK instead.
# Do not simply export all your public functions/methods/constants.

# This allows declaration    use TYPStats ':all';
# If you do not need this, moving things directly into @EXPORT or @EXPORT_OK
# will save memory.
our %EXPORT_TAGS = ( 'all' => [ qw(
    
) ] );

our @EXPORT_OK = ( @{ $EXPORT_TAGS{'all'} } );

our @EXPORT = qw(
    
);

our $VERSION = '0.01';


# Preloaded methods go here.

# Autoload methods go after =cut, and are processed by the autosplit program.

1;
__END__
# Below is stub documentation for your module. You'd better edit it!

=head1 NAME

TYPStats - Perl extension for blah blah blah

=head1 SYNOPSIS

  use TYPStats;
  blah blah blah

=head1 DESCRIPTION

Stub documentation for TYPStats, created by h2xs. It looks like the
author of the extension was negligent enough to leave the stub
unedited.

Blah blah blah.

=head2 EXPORT

None by default.



=head1 SEE ALSO

Mention other useful documentation such as the documentation of
related modules or operating system documentation (such as man pages
in UNIX), or any relevant external documentation such as RFCs or
standards.

If you have a mailing list set up for your module, mention it here.

If you have a web site set up for your module, mention it here.

=head1 AUTHOR

Hope xxxxxx, E<lt>hope@E<gt>

=head1 COPYRIGHT AND LICENSE

Copyright (C) 2010 by Hope xxxx

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself, either Perl version 5.10.0 or,
at your option, any later version of Perl 5 you may have available.


=cut
```

But I don't know what to write and where to write it!

---

### Post by Puzzled Guy on 2010-01-22
Never mind. I found out how. I added the code and wrote a program to use it and it worked. I even managed to install that module!

---

