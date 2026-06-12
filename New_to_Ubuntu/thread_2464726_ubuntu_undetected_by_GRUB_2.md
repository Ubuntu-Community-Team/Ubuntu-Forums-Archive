---
title: "ubuntu undetected by GRUB 2 ?"
date: 2021-07-10
forum: New to Ubuntu
---

### Post by aherve886 on 2021-07-10
Hello everyone! I am a new Linux user and I installed Ubuntu 20.04.2 LTS on my laptop with Windows 10 (dual boot).

My laptop: HP Envy Notebook with UEFI boot
My installation: 
[LIST]
[*]Ubuntu with GNOME installed on live USB (I followed [this tutorial]("https://l.facebook.com/l.php?u=https%3A%2F%2Fitsfoss.com%2Finstall-ubuntu-1404-dual-boot-mode-windows-8-81-uefi%2F%3Ffbclid%3DIwAR0G431h2KboBm3fWw-ilXgsr-9aumiMfb20ZGxwOS0KGChVNCS1YkZwjY8&h=AT1iToh8T4gm3FdDeJjRLpUJzA5chAf5SAU4Y6rf4TZxew75dJCj4VsxOH0eVBeeqry88frWVX2h9Xkzk6-1KjQuK7vFmkcrJUwpHPBucMKbF5OwBCzxcAYETAXBHmig6ivC7KwVxtPplA") with Approach 1 at the end).
[*]Ubuntu installed on a partition of my D drive (SATA 1 To) (Windows 10 on C drive)
[/LIST]

The thing is I can not choose which OS I want to boot at boot/reboot-time. 
Indeed, Windows 10 starts at boot-time and I do not achieve to press any key to have the GRUB GNU 2.04 menu.

According to [this website page]("https://help.ubuntu.com/community/Grub2?fbclid=IwAR1ickbrnU0ImoSAlvoP8boPiQFZIwKkqn6Q9ILXiD611PMutiW_xGAxaMg") (Boot Display Behavior part --> Initial Default subpart), it seems like GRUB 2 only detect the Windows 10 OS.
Does GRUB 2 only detect OS that are stored inside the C drive?

Can you help me having the GRUB menu while booting/rebooting my laptop?

Many thanks.

---

### Post by tea for one on 2021-07-10
> **aherve886 said:**
> Ubuntu installed on a partition of my D drive (SATA 1 To) (Windows 10 on C drive)

From your description of C Drive and D Drive:-

Are they separate physical drives?
Or separate partitions on one drive?

If they are separate physical drives, assuming Ubuntu installation is in UEFI mode, you should be able to boot both systems via the UEFI boot menu.

Alternatively, you can run a boot-repair report - Second option [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Please do not attempt a repair yet, post the link to the report.

---

### Post by yancek on 2021-07-10
I would suggest you read the official Ubuntu documentation on dual booting with windows at the site from the link below.  Compare the instructions with what you did and you may see the problem.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The most likely scenario pointed out above is not installing Ubuntu in the same mode as windows, both UEFI. 

>  Does GRUB 2 only detect OS that are stored inside the C drive?

The above comment indicates that you are not familiar with Linux or Grub device/partition naming conventions.  The C, D, E names for devices or partitions used in windows was copied from other operating systems in the 1970's and is not used by LInux so that those letters don't mean anything in Linux or Grub.

If your machine is UEFI, look for an entry for Ubuntu in the BIOS firmware.  If there is none, that's the problem and you should run and post the output link from boot repair suggested above.

---

### Post by aherve886 on 2021-07-10
Hi tea for one! Thank you for your quick response!

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAbYAAABNCAYAAADKK0EeAAAABHNCSVQICAgIfAhkiAAAABl0RVh0U29mdHdhcmUAZ25vbWUtc2NyZWVuc2hvdO8Dvz4AABwqSURBVHic7d15XFXV3sfxz EchsMk8yiDIIpiCpljDjmS4lBqOaZm5k2z0bLyampolt5KzW5W lRYqTmkmd5UKudyQFHDASURJwQH5pmznj9ABTyHQVOv3N/79eIPOHtYa6Pry1p77bU1SimFEKJWi4mJoXnz5ve6GELcFWb3ugBCCCHE30mCTQghRK0iwSaEEKJWkWATQghRq0iwCSGEqFUk2IQQQtQqEmxCCCFqFQk2IYQQtYoEmxBCiFpFgk0IIUStIsEmhBCiVpFgE0IIUatIsAkhhKhVJNiEEELUKhJsQgghahUJNiGEELWKBJsQQohaRYJNCCFErSLBJoQQolaRYBNC3HnFVzi8 n1Gdwyi85x4ik1vyOH32uPh6oKLiwsujjaYW9ji6FLyvatnZz48VgzksnliS4J8vfCq64Ofvz9 fvVp3nsC3x3JqaQghWx5wQ bOqXHL/1yazyBLYXG9yhIWMbTjWyw7beUjHKfKC7vmsvwtgG4Ojjg4BZEx2c/Z3 GKl jc5t4Z0BzfJ0dcHD0IuTRV1h2PK aF 4eUWnsX/wiEWH18PJwx9XJASf3AFq/uoGrqsK2mRsZ28ybFq9uJffaz7J/4Glf1 vX195Ki5X9tevtit Y9eSXblqwbwrtvRszYvUVKh761ssvhKj19u3bd4/ObFCXt8xUvUNDVMdRkSpycLBqMSNOFVVz78LYt9WDrWaqIzftkKm 7eetRm3IK3OqLHVy1XOqafCLakuOqSPmqbUjQtT4Xwuqdf7ic6vVqAfbqBde66vq9vlaXS372fklqp9fC/Xy2gSVZVCqOP2IWjq6iQoYsVZdNpRuVHRcfdTRT3We/qs6l6eUKryk9n06QNUPmaC2Z1erCPeAQV1c qTye hl9WNCpiq 9uPCLJWakq4KK2x74auBqt/8tWpyh8Fq fWKl5Wjlg9wVUN yDPyWYb6aUwPNW3th rRHgtUYrGRTW6B9NiEEHeQBr1fBLM2H2DL4jfp09AGzd94bDRljqaxIfCx1xju8gsbDheZ2CeP9Axz7O2rUYqCI8wfORPeXsXs7u5oy31o4NTSzzncZzaz gRgowEz 0YM nAm7bYsZNXFkr5HUcz/sSj7GeZN6oSXJaBzpvk/PuYt/xUs3JR5a9W 4wr4Y/1Wmo5/m14BtjeG9XQ2uLjaoyu7qeE0K1YqHhvUk2ERySxZdR5DDc6kLv/Et2e7MqznYJ6w J5vj5nuy9eEBJsQ4o7S zcjxMX87pxMKZTSlMu7cgwZpGfZYm9XVbAVcmT CywPm8e8vp5GGsoc9v0ez4MdWmBV9se2bekYEsvOmALAwIU9e8lt3Z6GZdNA48rD7b3ZvysOY6OfhjML6N5xJtE/vsMTLQPxazudfUXFxH8 gBAfbzxd7dDrrbF3D6LtoOmsO1VQbt/wR6axevFLRLRsQsN6XviGDWLunkuciZ7NiI4h1Pevi2e9Noz  iiVDohWI/uLE1byk3UferroCOoXQfaK1ZypdrIpUtetJC28H/V07vTu58y6ZYcw9SdJTUiwCSFqh JM4lfP4ZusnvR9QGd8G5VBWqYtdewqb/oMZ79h0rJGzJj8MLZGz3WBpPMOeHlalP 5xh4vTw1nT1/CQDHnTl/AzdujQkOrxdPbleTEM0aDDaDw4EdMXOnGhHVHOb1rKg/ptDQYOoBGZhF8fS6T3NxsUuPW8FbwDp7vNYkdZW4rFsR8waeJ3Zj/22GOn0pkxyRLPun7II8vKGZY1D5OJp4lYcNwUqY z enjKWQBW36dOLw3LdZk1DZ/cpiEtZswPrRbjhpwKxeL8Lz1rHubDWTTaWyfm0ajzzqgxkaXMJ74bppLXF/Q7JJsAkhqqSUIjIykv79 xMZGYlSf9tt/ltnuMLSIb54eHjg4eGGg60jwcO30 6912ltZWIfVUBx4V4mh3ni6emFT4OW9H5 Adsvlh0Cy2f3/E8oHPMGnexMHSebrBwrbPQVuzUa9NZ6crKyUSiys3Kwsra qfNjaW0N2VnkmriMZp7Dmb/oOVq7WxjfAA2WLiH0fvtL3vJezuJfr0/bQBswnHen9iLQRgNY4PvYaCLsGzDy4zfo5qcHwLrRSEa1i eP2AKjx3YdsJCVYwuZ2y2I4M7DmfTJOg5dqhDDhiQ2/KyjSxeXkvppAwnvlM7GTanVmgSirmxiw8V2dA8oGeTVuHaju300/zl5 8OREmxCiCrNmDGDqKgooqOjiYqKYsaMGfe6SGDmxODvkkhOTiY5OYW0zEscW9GXg8 P4sskE70GXRhT913iUnIyFy6c59Tebxnn8gNDe81k/7U2PnMjn21sxtjBPrfYQFarWQeNxuRon8bCCqvqnNzMg1YtnTlx9GyZmaYVjquxw962mKJyeaHF1s6cvBwTfUZNHZo/u5CtJ46yftqj1In7hCeahjEiKp5rl0ld3Mzmoi50875WUB2NO7cicfMW0qtR9Oxtm0hsG07Itc61mRePtC/il ia3aczRoJNCFGl2NhYUlJSyMjIICUlhdjY2HtdpJvpHGjQaxrTH40janVStRpHXZ0gekz5kKeLlrJ0f0kjn/nLSva1fpIupnprABobbK3zyL6py6XIzc7D2tYGDRpsbK3Jy8m5KerycnLRWNtgddszaTTY2tuSl33zOW5yK51srT2BHYbwxr9/JnbjMP568w2 Ty05UMa2aHYfmkd4oD/ /iVfDYYvJ2nXb zNr K45LN781bilwwmyP/a/oH0 vQYMb/tqPBYRc1JsAkhqhQaGoqbmxv29va4ubkRGhp6r4tkgo66vu5cvpha/b/6td74eaVz6bICirl4 jyX1z1LI/8yDfZTSzkXPYGwh6ezpwjQeuDjmcb5CxWG8lQG55MN1PV1wQwt3r4epJxLrlCWYpLPpeDu58PtT6kpDVI72zvemOsbP0aE33EOJhQBBRzYEUf4ongSExNvfJ2K4d1Ge9l2pIobZcXx7NzXiPdjE8vvf/xzuh/exr4qg7FyEmxCiCpNnjyZ4cOH07VrV4YPH87kyZPvdZFMMJCSfBknN5fqN25FpziZ5I6Ptxmgpf5L0Vw4n1SuwY1fMhjvrh9wYOdUWuoArHmodX32b9tbfmZh1u9si2tG2 YWgBmeLVtg9cd2jpdt51UqO7efI6xNyO0Hm8rkSNwV6gd73fnG3JDGlXRr7GzMoPgv/tjvRGhTffltzNxp2jiLvXsvVdpBVJf3sCe3KaEuFbqs1k1o6rSf3bd5n02CTQhRJY1Gw5QpU1i1ahVTpkxBY3I /b1USMof83l3jRu9e/gab9zyrpKSXnC90S3OTOA/01/nG8dhDG5iYialUVoCBj9L4zUT ef6RHIUGLLiWfHaP9nafgz9PUquj675SJ62WsTL728jOR8ovkrsopeY9Vd//hFe2VinCfnnOJ6QXtoDLOD8xunMievBkI76KnasCUVG0jESUrKv37crzkrklzlTWWbZk4hgLeT ycELDWjiq62wr47gBwI5su QyRmfAEVxBzge2KT8YxAA2no0CTpLTGzWbdXg/gw2QzJ71/5ITErNbjHmxP/K6t9OUNkEViHEnaJBp9PV6AFtjdYcndEdNOjM0vhuoFeZpbHq0nL8Th76 FteDq7Y4JYwXPiRV9sH4urggJOzK16NezHrTC iVrxCo0pyTaO7uRxm3sNZ9O2TJEd2ws/RAeeAnnxcNJYVCx7H dq2uka88t1C2u57iRZeDji4NGbwCnemrXqXDjam6qxDZ6JlVkVJ/DihG00aNiCoXkO6vJfL88vep6ttJftqtOhuuhwazHWm ouKtD2fMT7iQQK8PXF1csA5oDOT9rdg/sp/0twcihOP8ZdXQwJvumYaHEKaYHfscJnn2TTozLVlfu KS/EnsQgKwvam360FjZoGcPLw8dt6nk2jbnnebhFJO9Zw2K4TPZs5l//HmpfAlvUJuHXtRuM6d Avu4JNjPF9jJQPLrJmaHX/6jGQOO8RGn/Wjm2H3uWhSv4Rq6tx/LK7gKbdwnAz/v9DiPtKTEwMzZs3v9fFELcjexkDGv/KmBOf093UUwACuK0eWx47PhjOkH/tpOKTEOrKZmY89Qz/3v93PEN txVzctFoevYewkf3ZfmFEOJ/W00GlWtIof6 tZrvIi0BQ fwf255PNz0Dl4eIYSoCY3OyJCiMOautdxFGWc4cugoiSkZFFk4Uy sFaHeZZ7Izz3Bbz8nU69nO9xSD7ArNhO/RzoQVDoIW3glnj27j3Ax3xqfkKzqTeVVOZyL/YP9p9Iwc2mAe7mupYGL 9YTY/4wj4bAiT9285f Qbo3d0ejdFi7uGBnAYazv7MmVk HiFBuTOBRpMdt4perDenVzp9rowIFqUfYvTeey8qBwIfa8IC75e1fOCGEALAewLK/BtzrUtwfbv3FAJnq28f0yn7YWlXxZQSGc5 qLnpvNe7X/JIfFGxVL/pZKGtnb1UvKEgFeDsoSwtP1W3OPpVVuk9x0sfqEX19Ff5kW VuYa5sXJqpN3cUKKUK1MlvRqjGdmbK0sFb dV1VtY6rdKaWam 32SYLJ3hynb1TmcPZa6zUa4 vsrD3kJptVqla/SW2luolFL5avNzXsq VT/1WENbpbOso7z6f6kuGJTK 2GIsrMbrFbnKVWw/RVVT99BzTtd9n0K Sr6OU l77FYpRpKvj 2eKCqb61Veue6ysfdVun0gWpwVEKFVzwIcW/cu9fWCHH33easSEXRub1s Oknfir7FX2YS2W7VOYdmJeYT/als/wVH0/C2UskLQ8n/p0pLEsuM1xZ/Bd/nHqIeQdSyUiNZdbD5hjOfs0Lz6/FZeJOzl86S KZS1xJXEzfSiel5LNrxtPMPB3OkuOXSEk6zYWrKex4/YEKXVRF1v4Y1LM/kZiWxrmVI/HQXP8IAF3wAzTSHOVgXJnunuEch/5MwzukMXU0YDj7NS /Go3/9L0kp5whKfkiByL9 M/EGWzKvp3rK4QQoqZueygyd/u/eGpPxYHfIvKLXHi4wk8L05OIP3GetPwiDGauuBVu5 ipIvAonXaqDWD0vH8xsPG1aaiKK9Fr2KYfwMoJrXEqPY2lqyfOFpBiqlCF 1nz4zlaPD VJwJKV0M1s8PDw 7mxUi7TWXxqx1vTM tQOPYiraNslj2 1GKeoShA1T672w/pKfVq00wR3Epei3b7Qex7oUw7M0ArGk8sB9hby/k9/gieobJvTohhLhbbrPF1WA3aBkpS/pQ9m6SOr QbvXLLJKqLrJx0kBGfbSTNFsXHK20YMjhcpE9bco9xWeGVls2YYpJOnkKQ71OBNXkdlV IgnnrAlq6F31tE tFm1lnT9tA7p28WHmr7 RNC2MADPI3bWZnbRjTnub0jImUuwUSOrv29im1aDRaNDkpFBkyCA9436cQCOEEPevu9KVyN8SyZj5aTyx9jSzw72wAFTKInr4V7VCuCIvNx8sLanJYxsqL5c8LLH8W Zu6Ajr2xvvBWtZl/QyL/nns3NdNHnt3yHcWQMo8vPyKDr6FeMHLS8fpM6N6OV8fz4DL4QQ96u7EGwGzu7fz6Umgxnb1atGAUXp6thkppNZg46PRm LjVkW6Rm3 /KDEhYthzCw3qcsX/kX48cl8P1PuYR/0Bc3DYAZtvZ2mDcbzbbf38TEggdCCCHukrvSnTC3sIC8XPLKzhNJu0J6lWGlxbdBINoTMcSW3bgwj7zKnp22DKSBXz4HY LKLMuiyM 7xSWjdc0YOiyEg19/xdZ1S1hn6MOICKfS 3Va6jVpjP7EbmKuyrCjEELca3ehx2aGV8fONHjjCyb/60H 2d2DzD9/ZO7Uf7G70IOWle6rweHRp hrPZSpz32EzQttqJO6h 8/nMXSK4oIU7vpmjFwyAPM/fAlJjaYxoDAIk5s/Jz3PtpLoU XW6iDluCR4 k6 1WGvpSHy6gtdCvzvnjb7qMZ6tKTN4ZMouDlHjRytaQ44yLncnzp2isUp//G9WKFEKKWuo0emxlWegvjC5paWKEvMyND13QCX38czpWFw nYthuj5h4mZMp0 jne2EZjboWVkdVONc6P8/EPs2h16iOe6tqR3i98zcUO4xjcoLJM1tH09eVEPW3Nhld707HLUGZsc2HkmE7cWHdUg5Xeymj5NVb6m14AqPEYwCvDHbmc3ZYXxj5YfkjVthOz10cxxOpnpg7tTvu2j9Bz0AvMXLSVM7f/lnMhhBA1cBuLIAsh7heyCLL4XyJT9oQQQtQqEmxCiDuv AqHV7/P6I5BdJ4TT8UR qLYTxnWqRkB3h64uTjh5BlMp9GfsPtK QEldXknc0e2J8jLHQ8PD oGd2LMZzFVTEQr5uLOBYwLb4qPoy029o64eNXnwYhZ7Mq9VoC9zOraCD9vL r6 OLn749fQFO6PbeQvWmmD160fwoPuPTmy/NGZmAXH P9VnUI/yLZ5HLw1a13 YuQxv7FLxIRVg8vD3dcnRxwcg g9asbuD5/LecY37/Vn1b1vfHwcMXZwRFX3zBGfXemdJ3dXKIntqKhnxcebs44Othj5 BJ467P8e/dl /L5evLuddregkh7rx7t1akQV3eMlP1Dg1RHUdFqsjBwarFjDhVVHGrtEQVdzJV5ZYuyVp4 bBaOqap8h2yQl0yXNsoVX0/yE899Mp6dTq35NjZCavV2KYB6pn16SZLkL1rkgrzaa9eW7ZPnc8uOYGhKEddPnNeXb1WkPyN6lnfvioqrcyOuWfU5rfaqsAhK2 UoYKCrS8qP3Mr1WrW0ZvqlLdzgmpobqlaz46/6bMa1bv8Huri0ieV30Mvqx8TMtX1FWwLs1RqSnrp2rSZavO4INVoxBL159UbZy7KuawuXr22sm m vZxDzVsbW6ZAqeoA9 NVy3qdlAf/Hl/r3IrPTYhxB2kQe8XwazNB9iy E36NLQxPmGrjh NA12wKm2RdE5NGDh9HMFbf2bvtdWJCmPYtCOEsZN64GtVcmzrgL68NdqfbZsOUmjkuKiLLJsZhU/kcmYPbI6ndckJNFo9TnU9cajw3Gm5slnVpevEfxCyZT27jR4cVFYWmg7dsF2 iN3lnibKYOOirdQPb0pBVo7JHlC16l1OAX s30rT8W/TK8D2xpCbzgYXV/uSae6FB9kQ7caoyUMIKVNBrd4JN4fyq1aYmZWpsaUroYPnEvV8AfPmRpPL/UuCTQhxR n9mxHiYl71hhWognwKLMvOUNZhbq5BUyEZDUphbm7i Dk72LwvlH69PIzP4K6qDEqhNBqT xZnZ0G9YYxuspEvNmbc2O/CShYf78G47o7kZmfXaGjv5nobUUVlNBUvUrVpCeoVgduuXzl0H79nWYJNCPHfR11i83tfcHXAEFpdyyyL1gzodYYvZm3gVI4CismIX817URk8NiAMY9FWfPYEifb1CbSveUOvcpLY9N5nnAh/nDZGc1ORm52LhbUHPUd3Zv ilVxQAMXEL4kid BIWtlbklNJj61a9S7HgjZ9OnF47tusScgxfgzzUCK6pbJoWhR/ptd89SWtf318kxM4lVfjXf9rSLAJIaqklCIyMpL /fsTGRmJuoNPCanMQyweGc4b6RNYNr0N uuf2PDIpGk0WP04gXXscKxji1PwU2xt8y4TWhpfGFZlpJNpY4dtdXItfxPjG3jg4eGBh7sTtnX86b3UlylTe BgdH9FdlYOVtZ6rB8eTf L/8eS GIo2MPiVW6MGFwPa2s9eVnV67GZrndZGlwHLGTl2ELmdgsiuPNwJn2yjkOXyo5b2tD5/TVMc19G/0b1eXjgBD5csYfz1Q0qCzvsLbJIz7p/p5BIsAkhqjRjxgyioqKIjo4mKiqKGTOqWsD81uTEfcmIdgNZ 8ACflkykmCrMh8WxPJ v4kkP7OehKsZXE3P5NKRZfQ9NI6Bn9w807KEAoOB6/2W4jjmdKqLp4cHbk5u9ItKvRE6lt1ZEJ9McnIyyRevkHH1FJuez DtIR/wp9FhuZJF2q1s9Gh0IYwYYc13i3eTuvELfgkdRV9XDWbW1pjl5VLVqF6l9a5IU4fmzy5k64mjrJ/2KHXiPuGJpmGMiIrn lsjrYMZ9MHPHDuxlQ f9OHsd6Np0eQx5u/PqqIkABrQKO7nqZESbEKIKsXGxpKSkkJGRgYpKSnExsb 7efI//Nj vVdiNvsX/nhtTZUfDFG4R9fstjsHyx4sxv1bM0AHQ7BfYn8cBApn33FASPpobGtg01WmUXUtSG8/ttZLiSfYfUIR3JyTS8NpLX145EJ7zEs9xuWHjQeTfl5BVjp9Wgww3fgMzRcN4Pn5v5J92e6YAto9Hqs8vPIryQkqqq36QLaE9hhCG/8 2diNw7jrzff4PvU8ifS2PjQqv/LfPhDDDveNDD75S9IqGp0siCDjHw77KvVzf3vJMEmhKhSaGgobm5u2Nvb4 bmRmho6N97gsJDzHlmLg4zfmB2uCfGXpJReOEcaT4B FT4UFuvPj4pZ7lgJKO0dQPxS48nvrLnwiqj9cbP8wrJqcbSQFGQX4ClvqR7pXHuzdheF9hnPoxRzUtukGmsrLEqzMfk8uvVqHd16Bs/RoTfcQ4mmOobmuPfty9NTxzkmIkZntcUJRzjlHsgAcbHQu8L8mpnIUSVJk eDJT03EJDQ69//3cp2LWIr8zGsP4JL5N/bevc3LE/f5rzBqhXZqPis4mcd/HEzVgq2Laje8sXWfHDGZ55zrfmf8kbUriQ6oib0W6UIj /sMyas9Y8MucAp8tsobHSY1VQ2mMz0gGqTr2rV840rqRbY2dj iiGtCukW9tRySZAIUfW/sSV9u/S9D5OB mxCSGqpNFomDJlCqtWrWLKlCm3MZ3cGAPnYw9j2a4jAZV0WSxaD WJqx/z0rwdXMgHUOQmRTNrwpeYDxpMmLGGWOPF4EkjSI4cwuvL93Mh51q3roiCgirG5IrTOBwVyVc5EfQ10coX5BWgszCxGDygsbDAvCCfAlVSz6S1Uxk/8z ULFRSvXqXp8hIOkZCSvb1e4rFWYn8Mmcqyyx7EhGsBXI4fzyeC5mFpbfJFLnnf ezSZ9xMbwPD5l68qLwKnErXmP0l85MnNDFxOSV 4MEmxDiLtGg0 mMhIAiPy XU//ugaeLCy5lvlz9/8GGazMi9G2JXLeAFnsm0r5eyZJa9bu9w8nuX/LDpFCTLzG2afcum5Y9SfaXo2hVtw42do64egbzfExj2gdbl5ZHh654I MCS8/t6oqL5wMMXeHB9BVTaW100qWi2GDA3Nx010ZjbYO MK90KLKYxK3fsuT730uDrZr1rnDOtD2fMT7iQQK8PXF1csA5oDOT9rdg/sp/0twcULnELX2dfq0a4OPphrOjIz6tx7Gh7lTWzO6G7bXfhTaL74d6l57TCUePJgxarHhu9XLGNri/35gsq/sL8T9AVvcX/0ukxyaEEKJWkWATQghRq0iwCSGEqFUk2IQQQtQqEmxCCCFqFQk2IYQQtYoEmxBCiFpFgk0IIUStIsEmhBCiVpFgE0IIUatIsAkhhKhVJNiEEELUKhJsQgghahUJNiGEELWKBJsQQohaRYJNCCFErSLBJoQQolb5fwr3Zw2/eMl1AAAAAElFTkSuQmCC[/IMG] *screenshot coming from the product specifications of my laptop*

According to my understanding and the screenshot above, yes there are two separate physical drives.

The F10 hotkey that normally allows to reach the UEFI boot menu just do not work at boot/reboot-time... 

As a consequence, when I start my laptop, Windows 10 starts by default without showing the UEFI boot menu.
Then, I have to perform an *Advanced startup* in Windows to finally access the UEFI boot menu...

You can imagine this whole process is not convenient.

---

### Post by tea for one on 2021-07-10
> **aherve886 said:**
> You can imagine this whole process is not convenient.

Yes, very inconvenient.

When you power on the PC, try [COLOR="#0000FF"]Esc[/COLOR] or [COLOR="#0000FF"]F9[/COLOR].

When you finally reach the UEFI boot menu, can you see an entry for Ubuntu (as mentioned by [COLOR="#0000FF"]yancek[/COLOR])?

If so, can you boot Ubuntu from this entry?

If you cannot boot Ubuntu, please supply the boot-repair report requested previously.

---

### Post by ajgreeny on 2021-07-10
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script using the live system which you used to install Ubuntu.

**Do not run the default repair or any other repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and the OSs installed.

---

### Post by ActionParsnip on 2021-07-11
Just because you have a second storage drive in your system doesn't make it a "D:\".
Windows uses letters to identify file systems. You can make 3 partitions that are NTFS and Windows will call them C:\ D:\ and E:\ even though there is only really one "drive" with 3 partitions. It's a common mistake by Windows users because the OS they have used mislabels file systems/partitions badly.

---

### Post by aherve886 on 2021-07-11
Hello [COLOR=#0000ff]tea for one[/COLOR]! Again thanks for keep helping me on this issue!

> **tea for one said:**
>  When you power on the PC, try [COLOR=#0000FF]Esc[/COLOR] or [COLOR=#0000FF]F9[/COLOR]. 

I tried what you suggested here but also F10 and it does not work, Windows keeps starting...

 Thanks to the link provided by yancek, I red that disabling the HP Fast Startup is supposed to help in this issue.
 So I tried, but it does not seem to work...

--------------------------

Hi [COLOR=#0000ff]ajgreeny[/COLOR], thanks for joining!

I performed the pastebin link upload. Here it is: [https://paste.ubuntu.com/p/5qkHnpzxwY/](https://paste.ubuntu.com/p/5qkHnpzxwY/)

Hope this will inform you enough to help me.

Have a nice day everyone!

---

### Post by aherve886 on 2021-07-11
I forgot to plug in the Live USB I used to install Ubuntu alongside Windows, sorry!

Here is the complete Boot-Info: [https://paste.ubuntu.com/p/VYhRFp2Wmn/](https://paste.ubuntu.com/p/VYhRFp2Wmn/)

---

### Post by tea for one on 2021-07-11
[COLOR="#0000FF"]Line 106[/COLOR] - SecureBoot enabled
[COLOR="#0000FF"]Line 404[/COLOR] - The boot of your PC is in Secure mode. You may want to retry after changing it to non-Secure mode

Please access your UEFI firmware and turn off Secure Boot.
Power off the PC
Then try [COLOR="#0000FF"]Esc[/COLOR], [COLOR="#0000FF"]F9[/COLOR] or [COLOR="#0000FF"]F10[/COLOR] again to see if Ubuntu appears in the boot menu?

You have to press the dedicated keys immediately after you have powered on the PC - try tapping F9 at one second intervals.

---

### Post by ajgreeny on 2021-07-11
I also see that you have an /efi partition on both sda and sdb whicn can cause difficulties when booting.

You should have only one on the computer to avoid confusion but I'm not sure how to deal with this after the event; wait to see what others say about this before doing anything else.

---

### Post by tea for one on 2021-07-11
[COLOR="#0000FF"]Line 93[/COLOR] - OS#1:   The OS now in use - Ubuntu 20.04.2 LTS CurrentSession on sda4

I've just noticed that you have booted into Ubuntu.

Did you boot from grub or UEFI?

---

### Post by tea for one on 2021-07-11
> **ajgreeny said:**
> I also see that you have an /efi partition on both sda and sdb whicn can cause difficulties when booting.

I think that it is a good idea to have EFI system partition on each drive because you can then boot each drive independently e.g. one drive fails or is corrupted?

---

### Post by yancek on 2021-07-11
>  I think that it is a good idea to have EFI system partition on each  drive because you can then boot each drive independently e.g. one drive  fails or is corrupted? 		 

I'd agree with that and it is also what many new users coming from windows want so they can have their OS's separate and independent.  The way the OP has it set up, s/he will only be able to switch booting from the two OS's from the BIOS firmware.  If s/he set the Ubuntu drive to first boot priority and ran update grub the problem would be solved as long as both drives are attached.

---

### Post by aherve886 on 2021-07-11
I did not understand that the hotkeys like [COLOR=#0000ff]Esc[/COLOR] or [COLOR=#0000ff]F9[/COLOR] have to be hit *immediately* after Powering on my laptop until now.

While rebooting my laptop, I hitted the [COLOR=#0000ff]Esc[/COLOR] key at the right time and I reached the UEFI boot menu, preventing Windows to start. 

Then, according to my understanding, the UEFI boot menu allowed me to reach the GRUB boot loader.
Finally, either I wait for Ubuntu to start or I hit [COLOR=#0000ff]Enter[/COLOR] key to launch Ubuntu.

--------------------
Interesting point, I did not have to disable Secure boot to resolve my issue.
--------------------

Many thanks for your help!

---

### Post by tea for one on 2021-07-11
> **yancek said:**
> I'd agree with that and it is also what many new users coming from windows want so they can have their OS's separate and independent.

Yes, also some of us Linux users like an [COLOR="#0000FF"]E[/COLOR]FI [COLOR="#0000FF"]S[/COLOR]ystem [COLOR="#0000FF"]P[/COLOR]artition on each drive and booting from UEFI firmware is almost impossible to break. ;)

An ESP is especially useful when installing to an external USB drive.

You know, de-activate the internal drives so that the new installation only sees one target drive.

---

### Post by grahammechanical on 2021-07-11
> Interesting point, I did not have to disable Secure boot to resolve my issue

Some on this forum always say, disable secure boot. But Ubuntu developers have gone to a lot of trouble to make it possible for Ubuntu and other Linux distributions to run on a secure boot enabled motherboard.

> Proper, secure use of UEFI Secure Boot requires that each binary loaded  at boot is validated against known keys, located in firmware, that  denote trusted vendors and sources for the binaries, or trusted specific  binaries that can be identified via cryptographic hashing

> On Ubuntu, all pre-built binaries intended to be loaded as part of the  boot process, with the exception of the initrd image, are signed by  Canonical's UEFI certificate, which itself is implicitly trusted by  being embedded in the shim loader, itself signed by Microsoft

[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

Regards

---

