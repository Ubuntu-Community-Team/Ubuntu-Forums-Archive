---
title: "How to start services on a system running without systemd?"
date: 2022-11-06
forum: New to Ubuntu
---

### Post by alekseylubimov on 2022-11-06
[COLOR=#000000][FONT=Roboto]Xubuntu 20.04

[/FONT][/COLOR][COLOR=#000000][FONT=Roboto]The system is installed on a smartphone and launched using a script:
```
[FONT=&amp]#!/data/data/com.termux/files/usr/bin/bash[/FONT]
[FONT=&amp]pulseaudio --start --load="module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" --exit-idle-time=-1[/FONT]
[FONT=&amp]cd $(dirname $0)[/FONT]
[FONT=&amp]## unset LD_PRELOAD in case termux-exec is installed[/FONT]
[FONT=&amp]unset LD_PRELOAD[/FONT]
[FONT=&amp]command="proot"[/FONT]
[FONT=&amp]command+=" --kill-on-exit"[/FONT]
[FONT=&amp]command+=" --link2symlink"[/FONT]
[FONT=&amp]command+=" -0"[/FONT]
[FONT=&amp]command+=" -r ubuntu20-fs"[/FONT]
[FONT=&amp]if [ -n "$(ls -A ubuntu20-binds)" ]; then[/FONT]
[FONT=&amp]    for f in ubuntu20-binds/* ;do[/FONT]
[FONT=&amp]      . $f[/FONT]
[FONT=&amp]    done[/FONT]
[FONT=&amp]fi[/FONT]
[FONT=&amp]command+=" -b /dev"[/FONT]
[FONT=&amp]command+=" -b /proc"[/FONT]
[FONT=&amp]command+=" -b /sys"[/FONT]
[FONT=&amp]command+=" -b /data"[/FONT]
[FONT=&amp]command+=" -b ubuntu20-fs/root:/dev/shm"[/FONT]
[FONT=&amp]command+=" -b /proc/self/fd/2:/dev/stderr"[/FONT]
[FONT=&amp]command+=" -b /proc/self/fd/1:/dev/stdout"[/FONT]
[FONT=&amp]command+=" -b /proc/self/fd/0:/dev/stdin"[/FONT]
[FONT=&amp]command+=" -b /dev/urandom:/dev/random"[/FONT]
[FONT=&amp]command+=" -b /proc/self/fd:/dev/fd"[/FONT]
[FONT=&amp]command+=" -b /data/data/com.termux/files/home/ubuntu20-fs/proc/fakethings/stat:/proc/stat"[/FONT]
[FONT=&amp]command+=" -b /data/data/com.termux/files/home/ubuntu20-fs/proc/fakethings/vmstat:/proc/vmstat"[/FONT]
[FONT=&amp]command+=" -b /data/data/com.termux/files/home/ubuntu20-fs/proc/fakethings/version:/proc/version"[/FONT]
[FONT=&amp]command+=" -w /home/semen"[/FONT]
[FONT=&amp]command+=" /usr/bin/env -i"[/FONT]
[FONT=&amp]command+=" MOZ_FAKE_NO_SANDBOX=1"[/FONT]
[FONT=&amp]command+=" HOME=/home/semen"[/FONT]
[FONT=&amp]command+=" PATH=/usr/local/sbin:/usr/local/bin:/bin:/usr/bin:/sbin:/usr/sbin:/usr/games:/usr/local/games"[/FONT]
[FONT=&amp]command+=" TERM=$TERM"[/FONT]
[FONT=&amp]#command+=" LANG=C.UTF-8"[/FONT]
[FONT=&amp]command+=" LANG=en_US.UTF-8"[/FONT]
[FONT=&amp]command+=" LANGUAGE=en_US.UTF-8"[/FONT]
[FONT=&amp]command+=" LC_ALL=en_US.UTF-8"[/FONT]
[FONT=&amp]command+=" /bin/bash --login"[/FONT]
[FONT=&amp]com="$@"[/FONT]
[FONT=&amp]if [ -z "$1" ];then[/FONT]
[FONT=&amp]    exec $command[/FONT]
[FONT=&amp]else[/FONT]
[FONT=&amp]    $command -c "$com"[/FONT]
[FONT=&amp]fi[/FONT]
```

[/FONT][/COLOR][SIZE=2][COLOR=#000000][FONT=Roboto]The system starts without systemd, so all commands using systemctl end with the error:
[/FONT][/COLOR][/SIZE]```
[COLOR=#000000][FONT=&amp]#systemctl status snapd.service[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]System has not been booted with sysmtemd as init system (PID 1). Can't operate.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Failed to connect to bus: Host is down[/FONT][/COLOR]
```

[SIZE=2][COLOR=#000000][FONT=Roboto]How can I manage services (and for example run snapd, without which a large number of packages are not installed)?[/FONT][/COLOR][/SIZE]

---

