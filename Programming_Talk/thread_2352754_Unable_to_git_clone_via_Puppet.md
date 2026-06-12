---
title: "Unable to git clone via Puppet"
date: 2017-02-15
forum: Programming Talk
---

### Post by raja.genupula on 2017-02-15
My puppet master has code as below 
```


    vcsrepo {'/var/www/html':
                    ensure => 'present',
                    provider => 'git',
                    source => "https://github.com/wikimedia/mediawiki.git",
                    revision => 'REL1_23',
                    }
            file {'/var/www/html/index.html':
                    ensure => 'absent',
            }
    
    
            FILE['/var/www/html/index.html'] -> Vcsrepo['/var/www/html']



```

And I am unable to do git commit while running puppet agent as below 


```
    puppet agent --debug --verbose --no-daemonize --onetime



```And I am getting below error ```



    Notice: /Stage[main]/Apache/Apache::Vhost[default]/File[/var/www/html]/ensure: created
    Debug: /Stage[main]/Apache/Apache::Vhost[default]/File[/var/www/html]: The container Apache::Vhost[default] will propagate my refresh event
    Debug: /File[/etc/httpd/conf.d/15-default.conf]/seluser: Found seluser default 'system_u' for /etc/httpd/conf.d/15-default.conf
    Debug: /File[/etc/httpd/conf.d/15-default.conf]/selrole: Found selrole default 'object_r' for /etc/httpd/conf.d/15-default.conf
    Debug: /File[/etc/httpd/conf.d/15-default.conf]/seltype: Found seltype default 'httpd_config_t' for /etc/httpd/conf.d/15-default.conf
    Debug: /File[/etc/httpd/conf.d/15-default.conf]/selrange: Found selrange default 's0' for /etc/httpd/conf.d/15-default.conf
    Debug: /Stage[main]/Mediawiki/File[/var/www/html/index.html]: Nothing to manage: no ensure and the resource doesn't exist
    Debug: Executing '/usr/local/bin/git clone https://github.com/wikimedia/mediawiki.git /var/www/html'
    Error: Execution of '/usr/local/bin/git clone https://github.com/wikimedia/mediawiki.git /var/www/html' returned 128: Cloning into '/var/www/html'...
    error: RPC failed; curl 18 transfer closed with outstanding read data remaining
    fatal: The remote end hung up unexpectedly
    fatal: early EOF
    fatal: index-pack failed
    Error: /Stage[main]/Mediawiki/Vcsrepo[/var/www/html]/ensure: change from absent to present failed: Execution of '/usr/local/bin/git clone https://github.com/wikimedia/mediawiki.git /var/www/html' returned 128: Cloning into '/var/www/html'...
    error: RPC failed; curl 18 transfer closed with outstanding read data remaining
    fatal: The remote end hung up unexpectedly
    fatal: early EOF
    fatal: index-pack failed

```

Strange thing is 


    ```
/Stage[main]/Apache/Apache::Vhost[default]/File[/var/www/html]/ensure: created

```

and


    ```
Error: /Stage[main]/Mediawiki/Vcsrepo[/var/www/html]/ensure: change from absent to present failed
```

Any idea ? I am not git expert.

Thank you.

---

