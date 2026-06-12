---
title: "i switched to brave browser and get no sandbox"
date: 2018-12-21
forum: New to Ubuntu
---

### Post by newblank25 on 2018-12-21
I don't get this message when using chromium but when I switched to using brave browser and get no sandbox when I  open it up. i used google for answer but it wasn't helpful. Any help would be appreciated.

---

### Post by #&amp;thj^% on 2018-12-21
The Brave Devs are aware of this: [https://community.brave.com/t/unsupported-command-line-flag-no-sandbox/40069/3](https://community.brave.com/t/unsupported-command-line-flag-no-sandbox/40069/3)

I found a temp workaround for Debian via:
```
sudo apt-get install chromium
ln -s ../chromium/chrome-sandbox /usr/lib/brave/chrome-sandbox

```
You already have chromium installed so all you will need to do is;
```
ln -s ../chromium/chrome-sandbox /usr/lib/brave/chrome-sandbox
```
**EDIT:** If you have the need to revert this use:
```
unlink ../chromium/chrome-sandbox /usr/lib/brave/chrome-sandbox
```

---

### Post by newblank25 on 2018-12-21
i have chromium installed. i tried ln-s and I got this
ln: failed to create symbolic link '/usr/lib/brave/chrome-sandbox': No such file or directory
How is this fixed thx for help

---

### Post by #&amp;thj^% on 2018-12-21
> **newblank25 said:**
> i have chromium installed. i tried ln-s and I got this
ln: failed to create symbolic link '/usr/lib/brave/chrome-sandbox': No such file or directory
How is this fixed thx for help

Well this will be up to the developers to fix.
This from the brave devs:
> NOTE: If Brave does not start and shows an error about sandboxing, you may need to enable userns in your kernel. Running with the --no-sandbox flag is NOT recommended!
Myself I would not do this** "enable userns in your kernel"** I would just get rid of the browser. (Just my 2 cents worth)
On my end I see no sandbox warnings:
```
$ brave
Error: unrecognized flag --icu_case_mapping
Try --help for options
[20056:20056:1221/100312.742297:ERROR:sandbox_linux.cc(344)] InitializeSandbox() called with multiple threads in process gpu-process.
Crash reporting enabled
[20025:20025:1221/100315.484540:ERROR:CONSOLE(34718)] "(node) warning: possible EventEmitter memory leak detected. %d listeners added. Use emitter.setMaxListeners() to increase limit.", source: chrome://brave/usr/lib/brave/resources/app.asar/app/extensions/brave/gen/app.entry.js (34718)
[20025:20025:1221/100315.484663:ERROR:CONSOLE(34718)] "(node) warning: possible EventEmitter memory leak detected. %d listeners added. Use emitter.setMaxListeners() to increase limit.", source: chrome://brave/usr/lib/brave/resources/app.asar/app/extensions/brave/gen/app.entry.js (34718)

```
I'm now wondering if you have installed the snap package?
To check:
```
 snap list brave
```
And this also:
```
apt policy brave
brave:
  Installed: 0.18.36-1
  Candidate: 0.18.36-1
  Version table:
 *** 0.18.36-1 100
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2018-12-22
After further research I found this on my testbed:
```
User namespaces are not detected as enabled on your system, brave will run with the sandbox disabled
```[B]
^^^^^^^This is not ideal[/B]

Also please note on my system:
```
sysctl -a | grep usern && uname -r
sysctl: permission denied on key 'fs.protected_fifos'
sysctl: permission denied on key 'fs.protected_hardlinks'
sysctl: permission denied on key 'fs.protected_regular'
sysctl: permission denied on key 'fs.protected_symlinks'
sysctl: permission denied on key 'kernel.cad_pid'
sysctl: permission denied on key 'kernel.usermodehelper.bset'
kernel.unprivileged_userns_clone = 1
sysctl: permission denied on key 'kernel.usermodehelper.inheritable'
sysctl: permission denied on key 'net.core.bpf_jit_harden'
sysctl: permission denied on key 'net.core.bpf_jit_kallsyms'
sysctl: permission denied on key 'net.ipv4.tcp_fastopen_key'
sysctl: permission denied on key 'net.ipv6.conf.all.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.default.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.enp0s25.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.lo.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.tun0.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.wlp3s0.stable_secret'
sysctl: permission denied on key 'vm.mmap_rnd_bits'
sysctl: permission denied on key 'vm.mmap_rnd_compat_bits'
sysctl: permission denied on key 'vm.stat_refresh'
4.19.11.a-1-hardened

```
So in a nut shell as I understand it:
```
This toggle indicates whether CLONE_NEWUSER is available. As CLONE_NEWUSER
> +has many unexpected side-effects and security exposures, this allows the
> +sysadmin to disable the feature without needing to rebuild the kernel.
> +
> +When userns_restrict is set to (0), the default, there are no restrictions.
> +
> +When userns_restrict is set to (1), CLONE_NEWUSER is only available to
> +processes that have CAP_SYS_ADMIN, CAP_SETUID, and CAP_SETGID.
> +
> +When userns_restrict is set to (2), CLONE_NEWUSER is not available at all,
> +and the value is locked to "2" for the duration of the boot.
```


> Historically the security of user namespace was uncertain. eg: >>> [https://lwn.net/Articles/673597/](https://lwn.net/Articles/673597/) <<<[COLOR="#FF0000"](Please read this)[/COLOR]. If a user, as root inside his/her own namespace can trick the kernel into allowing an operation on the real host, there's privilege escalation. Usual non-user namespaces require explicit root (so admin) permission and so run what the admin chose: that's a known risk. A later mechanism was added in vanilla kernel: user.max_user_namespaces . When set to 0 user namespaces are disabled. The Debian (actually from Ubuntu) patch is still around, even if probably obsolete. Maybe for compatibility reasons
**[COLOR="#FF0000"]***Do this at your own risk:[/COLOR]**
To disable the message telling "that you're using an unsupported command-line flag --no-sandbox" you must enable user namespaces with sysctl:
```

sudo sysctl kernel.unprivileged_userns_clone=1
```

To make it persist after reboot:
```

echo kernel.unprivileged_userns_clone = 1 | sudo tee /etc/sysctl.d/00-local-userns.conf
```

End result was i was able to sandbox "Brave" only with firejail but still had the warning "you're using an unsupported command-line flag --no-sandbox"as seen in screenshot. _Again friendly advice I would wait for them to fix this and not cause yourself any grief_.:)
Kind Regards

---

### Post by #&amp;thj^% on 2018-12-28
Well they have fixed this issue now via:
```
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key add -

```
and:
```
echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ `lsb_release -sc` main" | sudo tee /etc/apt/sources.list.d/brave-browser-release-`lsb_release -sc`.list
```
also:
```
sudo apt update

sudo apt install brave-browser brave-keyring
```
However you will see a new banner warning "This Version of brave is no longer supported and will not be updated" along with the instructions i just posted.
Enjoy ;)
```
 apt policy brave-browser
brave-browser:
  Installed: 0.58.18
  Candidate: 0.58.18
  Version table:
 *** 0.58.18 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     0.58.17 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.58.16 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.57.18 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.56.15 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.56.14 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.56.12 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.55.22 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.55.20 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.55.18 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.55.17 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages
     0.55.16 500
        500 https://brave-browser-apt-release.s3.brave.com bionic/main amd64 Packages


```

---

