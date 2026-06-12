---
title: "Successful active directory login sends me back to login screen"
date: 2022-06-02
forum: New to Ubuntu
---

### Post by lastusername on 2022-06-02
I am installing a new Ubuntu 22.04 desktop, following the canonical instructions [here ]("https://pages.ubuntu.com/rs/066-EOV-335/images/Integration_Ubuntu_Desktop_Final.pdf")for adding the computer to the domain, adding it to the domain during installation.  The machine is able to pull correct account data from the domain ( # getent passwd \<username>@\<domain name> returns expected results).  Login requests are making it to the DC, as logging in using the wrong password several times will result in a lockout for that account from the domain.    
Using the kinit <domain user> and klist commands, I can verity I am successfully getting Kerberos TGTs.

The crux of the issue is as follows: when logging in, I have access for a couple miliseconds before I am kicked back to the login screen.  Attempting to log in on command line has the same results.  I can tell the login is successful because I am able to briefly see a warning about my password expiring before I am returned to the login screen. I can log in using the local account perfectly fine.

Has anyone experienced something like this before, or have any idea what might be causing it?

Edit to add relevant bits of log data from /var/log/auth.log:

SU to switch from built in account to domain account (Unexpected behavior):

    "May 24 16:44:42 <Computer name> su: pam_unix(su:auth): authentication failure; logname=<local account> uid=1000 euid=0 tty=/dev/tty3 ruser=<local account> rhost= user=<AD account>@<domain name>
    May 24 16:44:42 <Computer name> su: pam_sss(su:auth): User info message: Your password will expire in 6 day(s).
    May 24 16:44:42 <Computer name> su: pam_sss(su:auth): authentication success; logname=<local account> uid=1000 euid=0 tty=/dev/tty3 ruser=<local account> rhost= user=<DA account>@<domain name>
    May 24 16:44:42 <Computer name> su: pam_sss(su:account): Access denied for user <DA account>@<domain name>: 4 (System error)
    May 24 16:46:43 <computer name>su: FAILED SU (to <DA account>@<domain name>) <local account> on tty3"

Unsuccessful SSH login with domain account (Unexpected behavior):

    May 25 10:08:18 <computer name>sshd[32612]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.31.173 user=<DA account>@<domain name>
    May 25 10:08:18 <computer name>sshd[32612]: pam_sss(sshd:auth): User info message: Your password will expire in 6 day(s).
    May 25 10:08:18 <computer name>sshd[32612]: pam_sss(sshd:auth): authentication success; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.31.173 user=<DA account>@<domain name>
    May 25 10:08:20 <computer name>sshd[32612]: pam_sss(sshd:account): Access denied for user <DA account>@<domain name>: 4 (System error)
    May 25 10:08:20 <computer name>sshd[32612]: Failed password for <DA account>@<domain name> from 192.168.31.173 port 60699 ssh2
    May 25 10:08:20 <computer name>sshd[32612]: fatal: Access denied for user <DA account>@<domain name> by PAM account configuration [preauth]



Successful SSH login with local account (Expected behavior):

    May 25 10:11:22 <computer name>sshd[32625]: Accepted password for <local account> from 192.168.31.173 port 60750 ssh2    
    May 25 10:11:22 <computer name>sshd[32625]: pam_unix(sshd:session): session opened for user <local account>(uid=1000) by (uid=0)
    May 25 10:11:22 <computer name>systemd-logind[864]: New session 41 of user <local account>.

Unsuccessful SSH login with incorrect password from domain account (Expected behavior):

    May 25 10:19:58 <computer name>sshd[32711]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.31.173  user=<domain account>@<domain name>    
    May 25 10:19:58 <computer name>sshd[32711]: pam_sss(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.31.173 user=<domain account>@<domain name>    
    May 25 10:19:58 <computer name>sshd[32711]: pam_sss(sshd:auth): received for user <domain account>@<domain name>: 7 (Authentication failure)

---

