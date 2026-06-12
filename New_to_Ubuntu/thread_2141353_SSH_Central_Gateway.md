---
title: "SSH Central Gateway"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by thestrt on 2013-05-02
Hi

I have been asked to implement a central ssh gateway which would allow our devs to securely access our cloud instances, and also give us the ability control access to remote hosts.

I'm thinking of a service running on a host, that has SSH keys from each dev's machine stored on them, and then a SSH key stored on each remote host from the central server.

That way when someone leaves, we can takeaway their SSH key from the central server.  

In the firewall rules for each host we could set it to only allow access from the central server.

Does such a thing exist?

---

### Post by Lars Noodén on 2013-05-02
If they have read access to the private keys they can copy them and access from whichever machine they want.  And in order to access the "cloud" server, they will need read access.  Better to just add or delete the public keys in the /home/${USER}/.ssh/authorized_keys files.  The remote host ("cloud") functions as its own central server.

Something else you might look at on the server would be key revocation lists.  If you add the directive **RevokedKeys** to your ssh server's configuration and then point it at a file of keys, the keys in that file will not be allowed to log in.  More details are in [sshd_config(5)](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) but the basic format is one plain public key per line.

---

