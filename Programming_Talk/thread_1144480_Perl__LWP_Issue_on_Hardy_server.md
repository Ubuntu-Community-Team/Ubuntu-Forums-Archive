---
title: "Perl / LWP Issue on Hardy server"
date: 2009-04-30
forum: Programming Talk
---

### Post by matt.hilliard on 2009-04-30
Can't locate object method "new" via package "LWP:: Protocol::https::Socket

    my $request = HTTP::Request->new( 'GET' => 'https://...' );
    $request->authorization_basic( $user, $pass );
    my $reponse = $user_agent->request($request);

This code works fine on a FreeBSD machine, and Red Hat but there's something screwey about LWP on Ubuntu.

I've done both 
apt-get install libnet-ssleay-perl
and 
apt-get install libwww-perl

with no success
and I've updated both LWP::UserAgent and Crypt::SSLeay via CPAN,
with no success

Can anyone suggest what the issue may be or what a better forum to ask this question might be?

---

### Post by soltanis on 2009-05-01
You installed LWP via packages, or CPAN?

EDIT.
Maybe I should try reading, uninstall the perl packages and manually install them with CPAN.

---

### Post by ibuclaw on 2009-05-01
<- snip -> 
Must be too early in the morning, didn't see that you had tried Crypt::SSLeay

Regards
Iain

---

### Post by matt.hilliard on 2009-05-01
Great!  Definite progress.

I'm getting a 401 (Unauthorized) on the third-party site in question now, but the BSD and Red Hat machines get 200 using the same code--so there's still something off.

I suspect its related to the way authorization_basic() works, but I'm not sure if there's any known issues here on Ubuntu or if I need to compare the behaviours by packet-sniffing on non-https sites.

Still open to thoughts.

Thanks ahead of time!

---

