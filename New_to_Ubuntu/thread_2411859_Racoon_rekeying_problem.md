---
title: "Racoon rekeying problem"
date: 2019-02-04
forum: New to Ubuntu
---

### Post by mndeylami on 2019-02-04
Hi,
All traffic passing through my IPSEC tunnels stop exactly after one hour, although they show as established. In racoon logs you can see messages about expiration. I assumed this is about rekeying, but playing with the rekey option didn't help. This is the config.
Any ideas?
```
path include "/etc/racoon" ;
path certificate "/etc/racoon/certs" ;
log debug;

listen {
    adminsock "/var/run/racoon/racoon.sock" "root" "operator" 0660;
}

# Specification of default various timer.
timer
{
        # These value can be changed per remote node.
        counter 10;             # maximum trying count to send.
        interval 3 sec; # interval to resend (retransmit)
        persend 1;              # the number of packets per a send.

        # timer for waiting to complete each phase.
        phase1 30 sec;
        phase2 30 sec;

}

remote anonymous {
        lifetime time 2 hour;
        exchange_mode main;
       nonce_size 16;
        proposal_check claim;
        mode_cfg on;
        generate_policy on;
        ike_frag on;
        dpd_delay 30;
        rekey force;
        nat_traversal force;
        #passive on;
        verify_cert off;
        my_identifier asn1dn;
        certificate_type x509 "client.pem" "client.key" ;
        ca_type x509 "elastica_ca.crt";
        script "/home/madmin/phase1_up.sh" phase1_up;
        script "/home/madmin/phase1_down.sh" phase1_down;
        proposal {
                lifetime time 2 hour;
                encryption_algorithm 3des;
                hash_algorithm sha1;
                authentication_method xauth_rsa_client;
                dh_group modp1024;
        }
}

#
mode_cfg {
        network4 172.16.0.60;           # 1st address of VPN IPv4 pool
        pool_size 50;                   # size of the VPN IP pool: 253 addresses
        banner "/etc/racoon/motd";      # Banner message for clients
}

sainfo anonymous {
         lifetime time 2 hour;
         encryption_algorithm 3des;
         authentication_algorithm hmac_md5;
         compression_algorithm deflate;
}
```

---

