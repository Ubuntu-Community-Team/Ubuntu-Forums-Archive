---
title: "Reduce memory requirements, remove nm-applet, update-notifier"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by shreepads on 2008-07-14
Hi

Running a bit short of memory on my Xubuntu 7.10 installed on a P3 with 256 MB memory. Ran 'top' at the terminal and found 2 things I think (!) I can remove that take up a bit of memory, namely
- nm-applet: I hope removing this will not kill networking!
- update-notifier: I can run this manually occasionally

I did find something about killing and removing from the session start-up on the forums, but unable to figure out how to do the latter without some more newbie instructions for Xubuntu.

Complete top (sorted based on VIRT) as follows, any suggestions on what else can be safely removed (and how) would be welcome.

Thanks!
Shreepad 

```

Tasks:  78 total,   2 running,  76 sleeping,   0 stopped,   0 zombie
Cpu(s): 96.6%us,  2.4%sy,  0.0%ni,  0.0%id,  0.3%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    254916k total,   249388k used,     5528k free,     1536k buffers
Swap:   506008k total,    34208k used,   471800k free,    71252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                           
 5423 administ  25   0  137m  48m  20m R 70.8 19.5   4:56.38 firefox-bin                                       
 4341 root      15   0 89204  16m 7228 S  9.1  6.6   2:01.82 Xorg                                              
 4968 administ  15   0 86712  20m  10m S  3.3  8.1   1:06.46 xfce4-terminal                                    
 4896 administ  15   0 75668  12m 9016 S  0.0  5.1   0:12.20 xfdesktop                                         
 4900 administ  15   0 63796  13m 9036 S  0.0  5.3   0:17.26 Thunar                                            
 4908 administ  16   0 51880  12m 9540 S  0.0  5.1   0:13.15 nm-applet                                         
 4891 administ  15   0 44812  11m 6864 S  0.0  4.7   0:16.41 xfce-mcs-manage                                   
 4906 administ  18   0 43352  12m 8788 S  0.0  5.1   0:10.95 update-notifier                                   
 4880 administ  15   0 43216 6916 4476 S  0.3  2.7   0:10.54 xfce4-session                                     
 4914 administ  18   0 39148  12m 8416 S  0.0  4.9   2:03.23 xfce4-menu-plug                                   
 4905 administ  15   0 37300  10m 7148 S  9.1  4.3   0:29.07 xfce4-panel                                       
 4918 administ  18   0 35112 7460 5080 S  0.0  2.9   0:08.66 thunar-tpa                                        
 4959 administ  15   0 27272  10m 6864 S  0.0  4.1   0:23.86 mousepad                                          
 4894 administ  17   0 19164  10m 7248 S  0.3  4.0   0:11.13 xfwm4                                             
 4886 administ  15   0 16400 3388 2492 S  0.0  1.3   0:05.62 gnome-screensav                                   
 4321 root      15   0 13460 2816 2108 S  0.0  1.1   0:00.57 gdm                                               
 4317 root      15   0 13068 1556  984 S  0.0  0.6   0:00.37 gdm                                               
 4050 root      22   0 12556 2040 1780 S  0.0  0.8   0:00.37 NetworkManager                                    
 4097 haldaemo  15   0  5636 3660 2508 S  0.0  1.4   0:31.56 hald                                              
 4988 administ  15   0  5580 2968 1420 S  0.0  1.2   0:04.78 bash                                              
 4882 administ  18   0  5536 2720 1808 S  0.0  1.1   0:05.79 gconfd-2                                          
 4893 administ  21   0  4984  940  728 S  0.0  0.4   0:00.01 gnome-keyring-d                                   
 4869 administ  15   0  4436  544  280 S  0.0  0.2   0:00.00 ssh-agent                                         
 4064 root      15   0  3276 1276 1116 S  0.0  0.5   0:00.02 NetworkManagerD                                   
 4769 haldaemo  16   0  3260 1188 1036 S  0.0  0.5   0:00.18 hald-addon-stor                                   
 4098 root      15   0  3092 1008  880 S  0.0  0.4   0:00.09 hald-runner                                       


```

---

### Post by LowSky on 2008-07-14
you should really look into using another browser as Firefox is taking up almost 20% of your memory. Or you can try to reduce the memory it uses by altering a few things

look at this website for fixes
[http://internetducttape.com/2006/12/02/how-to-fix-the-firefox-memory-leak-firefox-hack/](http://internetducttape.com/2006/12/02/how-to-fix-the-firefox-memory-leak-firefox-hack/)

---

### Post by shreepads on 2008-07-17
LowSky

Thanks for the tip. I first tried to fix Firefox's memory reqmts via the link suggested, but didn't get very far. Firefox memory usage would climb to 200 MB after some browsing and would stay there, with little drops even if I closed tabs. This after setting the memory cache at 4MB, with pre-fetch off and 'back' history to 1 page.

Then tried suggestion 2 i.e. different browser. Had used Opera a long time back and decided to give it a whirl, esp as it is already available in 'Add/ Remove'. Much better results, memory climbs to 100 MB only if I mess around a bit and then to 170MB briefly if I start loading ultra-heavy pages. But it quickly slims this down, without me having to close tabs. Closing tabs makes an immediate difference.

Beyond this, the responsiveness is fantastic, quick rendering, new tabs, startup times much lowered and scrolling doesn't take ages. New top output (again ordered by VIRT) as below. I know some folks don't like Opera as it is Closed Source, but you can't argue with results like this...

The version installed from 'Add/ Remove' is 9.27, wondering whether I should bother upgrading to latest 9.51

```

Tasks:  79 total,   2 running,  77 sleeping,   0 stopped,   0 zombie
Cpu(s): 91.6%us,  2.8%sy,  0.0%ni,  5.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    254916k total,   249700k used,     5216k free,     1348k buffers
Swap:   506008k total,    34952k used,   471056k free,    60120k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                        
 4901 administ  16   0  132m  80m  15m R 61.3 32.4   4:58.26 opera                          
 4493 root      15   0 93324  20m 7728 S 25.4  8.2   3:14.00 Xorg                            4882 administ  15   0 86664  20m  10m S  3.4  8.1   0:29.60 xfce4-terminal                 
 4866 administ  15   0 75708  12m 8984 S  0.0  5.0   0:14.77 xfdesktop                       4870 administ  15   0 73180  14m 9720 S  0.0  5.7   0:30.13 Thunar                         
 4853 administ  15   0 43412 7016 4636 S  0.0  2.8   0:11.07 xfce4-session                   4876 administ  18   0 43252  12m 8796 S  0.0  5.1   0:14.37 update-notifier                
 4861 administ  15   0 40864 5908 3016 S  0.0  2.3   0:11.35 xfce-mcs-manage                 4877 administ  15   0 38912  11m 8256 S  0.0  4.8   0:17.40 xfce4-menu-plug                
 4875 administ  15   0 37472  10m 7224 S  0.0  4.3   0:31.62 xfce4-panel                     4879 administ  16   0 35144 7452 5072 S  0.0  2.9   0:10.58 thunar-tpa                     
 5044 administ  15   0 26980 9.9m 6756 S  0.0  4.0   0:13.20 mousepad                        4864 administ  15   0 19120   9m 7232 S  0.0  4.0   0:13.47 xfwm4                          
 4859 administ  15   0 16656 5372 4304 S  0.9  2.1   0:14.78 gnome-screensav                 4477 root      16   0 13464 2820 2108 S  0.0  1.1   0:00.58 gdm                            
 4474 root      15   0 13072 1556  984 S  0.0  0.6   0:00.42 gdm                             4034 root      15   0 12556 2024 1760 S  0.0  0.8   0:00.49 NetworkManager                 
 4081 haldaemo  15   0  5936 4104 2552 S  0.0  1.6   0:42.20 hald                            4884 administ  15   0  5584 2972 1420 S  0.0  1.2   0:07.00 bash                           
 4855 administ  18   0  5536 2712 1808 S  0.0  1.1   0:06.17 gconfd-2                        4863 administ  21   0  4980  940  728 S  0.0  0.4   0:00.01 gnome-keyring-d                
 4842 administ  15   0  4436  544  280 S  0.0  0.2   0:00.00 ssh-agent                       5020 root      16   0  3772 1004  604 S  0.0  0.4   0:00.77 mount.ntfs-3g                  
 4048 root      18   0  3276 1280 1116 S  0.0  0.5   0:00.03 NetworkManagerD                 4718 haldaemo  16   0  3260 1188 1036 S  0.0  0.5   0:00.66 hald-addon-stor                


```

---

