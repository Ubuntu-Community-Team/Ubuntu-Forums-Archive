---
title: "New to Ubuntu, need help with Samba"
date: 2023-05-14
forum: New to Ubuntu
---

### Post by kekkegg on 2023-05-14
Hello,

I am new to Ubuntu, coming from a Windows background ive always wanted to learn Linux. 

Im farming some crypto (Chia), so I figured that I could make my farming PC (alot of harddrives) as a Ubuntu setup.

I would like to transfer bigger files from my Windows PC to my Ubuntu harddrives.

Ill downloaded samba on the Linux system and confiured the samba.conf file, added:

[plot1]
path = /media/kekke/plot1/
valid users = kekke
read only = no


[plot2]
path = /media/kekke/plot2/
valid users = kekke
read only = no


I can view the folders on my windows computer, but when ill try to open them ill get this error message:

 Windows cannot access \\10.10.x.x\plot2


Check the spelling of the name. Otherwise there might be a problem with your network. Try to identify and resolve network problems, Click Diagnose.

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgUAAACiCAYAAADRGr5yAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAACHQSURBVHhe7d19cBTnfQfw3x2ujW0SQHUcj5O4gCRoVLlJsHGKhN2JCRQhT4IdI//haeQ6QUAbQLhDp7QkxVNaGjM1EqQBRF5MOmSmkmNrppbkQLCnxEBjx6SuNYrRG5jJ2CEQSbgxthPD9fk9zds3v77O3u3Ul3uu9n5kba92effXb32ed5dp/Yr0dGE1euJCiRuEIXzl gX557k2686SM07fppdP31H6Crr76aAAAAYHJ577136eLFMXrrrYt0ZniIyspmUuxX5y8kBDp79ixRIka3zJpDU6deqxYBAACAye7tt39Dr/38VStTcOH8efrNpUs0b161mgwAAAClJv7OO /QL8/9kv7gD8rVKAAAAChF8dHRUbrxwzejygAAAKDExS9dukTTpn1ADQIAAECpil96 2267vppahAAAABKVfz999 na66 Rg0CAABAqYpTLKb BQAAgFIWT1y5ov4FAACAYvSJT1TRj398VA2l42mf/OQfqSGzOAUsKPjkH3 cHtm4Xg1Zzpw5LcdPtPvuvYdOnDimhrz94Ml2mv6Ba5K/Qgg3AABALnzjG3vpSw9/0TNjwON42u7de9QYszh/zTCob39rX8abr5eWln Vv4n2pS vpov/9578/c///lyNBQAAKG533nkXffs730vLGNgZAp7G82QSV38D c53/53Wrv6yGgIAAIBC4c4YhM0QsDgFLyig225fQHcvXmJ86udSBL2InvG8//DVv5M/Hrd3z785qiG46J L9pleHeFelz0P42FeL//lZXS8vjBVA3YpBq Lw8Xb5XXo63FXPdilJXZ4eTkeDwAAMJH0jEHYDAELVVLAHt 5S97g3TdjHuZSBLt4/tlDz8mbZXPzX9Oj//jP8sfj16z9K3ruyOHkMsNDQ3Ts2Aty OWfvkQPPfxlOX7Z0rvplVdfS67v4b/487SqCx4/a9ZsNURye7NmzTFWDXD1h31j1zMmvD 8Lt43duRHh2nT32yW6 Ft8rbtcHCYOGz2/p8 PUy1tYvkNAAAgGIWOlPAuBrhkY3r1JCFb h8g7RvunzjtG/ bnPKy XNlpf56tceTc538OD3aMWKR4rv/Xb/icqfjJT/5bDZHMbOh2PLZd/rVv7F70NgX6fLxu3eLPLqGFC2vl/7xNfTqHidfDYWSzZ8 hL9zfIP8HAACYSHqVgV6VEFSk7xTYN8E333xD/rXpN13 mZ7YH3zwi/Jmy5kAu0qCMwlcaqBnBNw 9tGPqf/S8bKmTEg 3PyRj6j/AAAAJp67DYG7jUEQkb9TwMXreqNDvrlz8by7WoHxzfzs66 rIWveo//1vPyfMwErGx6QT/qcOWBe6 Iifh5vsmfft2TVA7cFyKVPf/pP5LZtHCYOm12SAAAAMNFMjQrDZgwCf6fAjW K9k2c8c2dqxU cesfJqsQ7AaJ9k2ex/FNleflJ/u7/vQzcjqvi vxOXPAeDq3SdDXxcN pQiMqxS4TYG9HTe9TYFpHjcOGXvQyHidsVAAAAFAL tMC6dWvTMgQ2O2Pwla sUWPMYl3d3YlFdy5WgwAAAFBsOGMQy0G3BZEaGgIAAEDhyEWGgCFTAAAAAFKojxcBAADA5BW5oSEAAABMLigpAAAAAClUL4kAAAAweaH6AAAAAKR44gpKCgAAAAAlBQAAAKDgOwUAAAAgxf7zmWcS99TXq0EAAAAoVSgpAAAAACkeQ6MCAAAAEPCdAgAAAJDiCXzSEAAAAAR85hgAAAAkfKcAAAAAJLx9AAAAABIyBQAAACAhUwAAAAASMgUAAAAgoZdEAAAAkOIxvH0AAAAAQhwfNAQAAACGLxoCAACANK4NDXu2tlHswZ/RoBqOavDAkzlZDwBEI8/lrafVEABMFqEyBcab tmfUe3tbbT6qBpOGqXWB3HxgPFwmlbf/iS1nlWDSabxHo4eMWc2eZpI4/av9sCommCQ7/ltxjDzfqfWx7/U RkiTvLOL5wAMN5CZQrq7i4nOjVCA2rYNvj8EB0Xf9uec9/8x6jvFFHT3bPlUN3WJkoc/BRVyCEYb5O7hGU2bVpH1Pwddxo0jdfYN RHhtQIF57 yCi1PCXS70/F76kFRLs7zDfufM/PMoS5Z vLVGWvj3 Pl1PbI/YNN0Cc5IFX vMPJwCMt3DVB3fNoSYaok7XCTtweoRq5pURPTNMPWqcdHSY2qicVtylhgHyqOIz5VTjToOCabxFPKmKG2vT49YNKd0ote4bopp1i2nDLWrULZ iA vK6PihMx4ZrHzPzzKFmTPg96fWx 5aTN33pDLu/nEyfjKFEwDGV8g2BTOoap77hD1Nnc UUcP220SGYZT6tSLJwdPiSUdkFirVsLsekof5aUg QdjFhx5PsnI5bbq7pII51sE/13bcVRheVSGO VSViL5d7wu0Yj 5ued3r f2I44LcZA4CDIPM8eBVY1TuXuE6NRLVGlYXsoQXsm0r8xnmjN8ruJrv/gOeixumUUN84Zom/sJ2zRemk37xBPqPmPGlUu7RPr zEw1bJE31VND1JVWBJ/v VmmMAdgjBMrraSlN6904JKT9AcAEyoeC9VN4kyqX1pGNDCm3QSGqW1eOdXfwhmGEWp/3r7IjFLXoRGqWTrLt7rg O4OaqTFqvhwCTXxRcN1Q1/ TDl128WL24m28cVFw/NU7p6ZmuenK6ll4HDyoiSrPRxPRZyREX8cF11rnFXVIZ7E7nuJqvlJTK2ze6k1lxd5MdSLf3n7Kic0 PwINWjFo933DNFybf9YpjhgQeLJHAczacPBJhoQT580bwEN8HRDNU6m8Pruq880Gb5D5da2 ff4TGq z77R MV3mGMh9nN1uccTtml8AGfHqFf96yDSezWNUN8ZNWzL9/yR6emb ceJM72pdOBzI89V ksPJwCMp/iVxBX1bzDuJ5ie54aIKmeIE9zKMCQvMmfPULvHE1Cae5bQsUZ7Hq7r1DMd6gLx GKqk8OCKlpNEk R29zz8EVo wKqeeZl62nUXe0hMzILqOUeLRMjL86qqkP X0ZVs6xJrK7RfBHbITIpTY/rxaBi 1ut SsatWJhIT2DIvjGgeI3T5A4CMg/vH776jNNhq MWrZrcXjXfGoRT6rymPjFd6hjIfCx9nrCNo0PZCbN1eIks3zPH5bIWN1 mNpEGnKULvjFiSO9iTh/WKQl07w5S3 GcALAuAlZUiDIYkf7ZurM1VsZBtUQ8cwIHQ9wsauZPUP9Z6mYLS5E9jqCtEmQ2/GYx/GkNZtWaPWUXK3BJRgbxA3PzsTIxpL3zLEuaiLjsUVkGJrvC1DMGSCMjmJVj4ZhvnGg M4TKA6CM4bXb1/9psnwqfi013t7BzWfIurlKia/ A5zLCRTI7psGtc5q8Uyy/f8IcjqnMPUu24lJba6n77NceJOb75pKRfpzzecADBe4onQnzTUSgT0p2smLwLW058sQbBvsgVAPvHKJ2uu1iCrBGNWmcrEWFUdepGlfFOCi00rVR2oqzg/GH7ycRebezcMKwz5DK9WBaT97KdRv/gOeyxk5tSjEZ1pfCQeJRi 8j2/By7St6tz9Kd XU7jJKIg4QSA8REPW1DA7KfULv3pWrKfyI/kpl6Qb9oeT1H8tkOSnCf9jYi0i6pdVHr0DLWLG1Q9l2CoxladR63GXl4XYHlDesqnGNS0faaenru1 lPZ DLXgsZBJpnC67evUae5 MV3xmNhk6ULXg0ODeP9OErGUmTJkmxLo0bY8j1/QFzas3yA6 9drfvdDHFy/PSY k/xS0tZpL/A4QSAcRHti4ayjn6U2rkhoauY0aqDHspYpB6IumA2b9aKjY8eoeUiw5EkL2oiI/KI3jp6lFo3vyQyLLdpFxrVEHLfEFGy8aNV6tG772XVWFKOFBezn9Fq/SIpi0cNTNvfKsLsvliK9Ta6GknmRMA48KqWcMgUXr99jTqN//WL7zDHQsPpUJZmqWGbabzZTKtB3u4jqYyIipem1Xa7B vtCOvd nzPH4Rq32Evn4FnnDxzWNteelpyiJz woUTAPIvWqZAlgiIi7NXQ0KZYRC0VxGjExfMgyuphVSxMf em2O1YtbwE TAulFabs9zewe1L3XXTapqj1Oq6kDh4lO ULnfkujd3aHWJX6yaNP8JOO5/dlifeJiyY0i WMscvxmogN5qj4IFAeqcZ cx6t PkB4jfsaYJpswe4xjfnFd5hjkWRqROfXuM7krsXqbQkVBvU2hLExXL7nDyh5HB0//cateMRJzbolVLXPXqaDmiuX Nb1Z5P AocTAPIu9nRnZ2LF5z vBgEmDy6arjx9W9rNzDS lKXiZAa1Pmjd0FG/D1B6wr99AFAkrEZ06e0PTONLGeIEABhKCgBAM4qSAoAShpICAAAAkGJPPfV04t57V6hBAAAAKFXxGAoKAAAAQIj4SiIAAABMNvGwHzkGAACAyQklBQAAACDh7QMAAACQ4glCBQIAAABw9QHyBAAAACCgpAAAAACkOFoUAAAAAMPbBwAAACAhUwAAAAASPl4EAAAAEkoKAAAAQMIriQAAACDF8UFDAAAAYCgpAAAAAAklBQAAACBFbGg4SK21MYrF1K 2VYxhPbQ6Vkut1kCWoqwrl9vPhh4O7f/BVqodz/D1rHYdH5NCibccs/df/Wp9d3Cc4iDvaaAAj2XgfY4a9mJKv35hneD98D1OxRTHEylcPPWsTl2fgl r8it8pkAmnErq25KgREL9DhB19ajp46rIEmrFBjqWOEYbKtRwXom4Wd5GTd3i BzbQM5NlsAJzhmC5b3UMmCn0wFqaK/UTrYJioOcp4EiOJY52ecSSLMTzXGcJmt8F9Z 1e2zr0/d1EQ1yevVsUAnS372JWSbgkFqbWymanGj2VenRjGRmDbow1AgaqiqUv1bUkQ63cYZIv1GVEEbDrQQNe8QpxIAAHgJV1Iw2EXtx5toRaYMwACXJngUg8hSBruIZLV2cXZWR6xOu2pzjkhMc0zgccupjY5Tc6VrWujt27zCoXJjPVHXqdNzdur/1lQRt2m9ta2t2nIuju3rYU7FjWO9rmm5iTf/fXEUkSW3p5bR4pUnDbbWeq4jVDyb0mlFPTXU9FL/YK7iwNqH1as5zKvFXz3tqv2zV8HLy4n6eEO6D7yv dkPOS5jGNR BDp HnGRnMcjbaeF3Wc/dZHTr9iCZxrVpe ve//M8aenC8UUVp3PsQp83ii8f6kweBwPOdEez39DpivJSs OfeUSO7v60hgnrvA4hq3/HXGbpOYLcA21lk3fr2Dxov5Prit9GXP4rO2EZtyeLX1fnGGppVrDscjoBz94KhHYQEuipqYlMaAG03UnmogSZM/T3ZQgahJj7Wk1iRZ7YTGtRg4MJFpqSP2vs e3pjdZK3FxrTPS9jU8f9qGXOvkOEiux7ROfbzf/2K99vbSwpra54GWGjFN206Scz7fsDm4p6mwRI03e3nPfdHp6/LappYOQodBY0ynelpyrdMzPJm2by3jCLMWBzU1NclpfAxTy6h16fMnmbZl4ppfhSmr/TDOp/PaTpDjZy1n77YzbXut0xB2B9dygc5RE9N2Mm3DHX9 52WQsOr/86DzWAWLdw2PD5M23dv33G6G7QjdTfr5FvRa5Q6HHrc6FSZtv4Kldef4YPHifzxT4bPX73ff8qKHy297On0Z5gqL8Vj4C9918vE GlD/equhlgOqDrtuBTURP5mJ/wf7xX8qV8O5n Uij9Mn1qSe6rYY6lDaGyupvWHAWV3hK T2dZVVVNO23CMHrK2zYgNtaTpOctEg6/Ql1rtJ7Zg7rDUtZE q2LBFTPMgt689EethCy2LeJMM 8KSDf44Z6tzb7OGGupVOogUBo0xnfpVqUSJAy3MnH56VTUU9nLzVsaRAJuEsMD1JXO6Xms3mltyj7mibL/QhzzIMcPx2v2zdtG8KekbZclHPUmEZ1hm1I7vjzOy/91qNkOFah4z1s2vQU4Njw LZO9cTcQ5296lhnjBM/2v6lEWEyXUODHPcg8RLgeLrDF/6 pclVXJmORQbh2hTI4tc26kwrygiqiURGRTWsEL MMXZc/GoMF6QoMmxfRP4xMf4ANcqE5F3qM0j9vepfKew FaMs9pGLwZaTWn6ARO45ohBhMKVTmQGtprmm64uvANvn7VI7dQ3yCdhA9XU8LDInvF3xX9p1zZje8pmmgq47n2HIt5DnaKQ06t5GVH7ryeExCJs2I6ujTS29tE1kdAdbt1FvQ72ViZgQAeIvL/GS6/tWVNGORcjvFFTQhi1N1LbcdcMUJ1VrpoxCxVyqFnlwDqCDuoCnjZdErufAMeomr6f3kEzb91Cx4RgNiCtDbzIbfFxkHtX/qmRD5uJCrDMUXu/xZtqh4pQPqOfTi9p 8uYnjsO2Ni2HmQvZ7uNAHx2vqSL5cC7jTo4NxxgGVx1gkp1O9To MW9lM4nHCnGqhBQ4Diqonh80Gu0TkId7qXNHHz9yiCFvjvSWbXz7CbrufIchSNoOLYtzNHAaNWzDTW3TfF4GWE/Oj0G0tBlFhdzQDtqhl0D4xkklVdVoT8I9ndmnicDxFyBeMh5PN6/7lula5SH09sw8j0UG4V9JrNtHiYEW6hUZA6u4TfwaSeSw1HSjOtonlqPmytRyMmchLuDHuqlaG 9 Qq/bZ71Olv6 fR2taFJFRN6P9RrT9jXJIsQYVTZXa1UaNVTdZz3NxcSNpbp7n7qxBFhnJGK93Vbmi9fZKHKsntUHavvJY1Ep8rYDdtj85Dje/NRtohZqpkperrGPqiOVFEQIA6fTbqLl9vwx SioveqTnziQJ6G4qdgnIA/3tvV6n5Ce6c2wLdVIKP2ako/9yPKY xLrDpS23TLtZxbnaOA0atqGm7VN83kZZD25Pwah0qbYfvB05cLF3dVt1Fa9RXv7xy9OUg bclonP NnyxR/6fuVOV4yHU9v5vtWJkG3F AYeR4Lf7GOJ59M3P FL6hBSMc5vG1UNTBe3xfwIHKKtZV9tCWROSHC5MStpDtXuF4FngyKJm0XwHWgiEza9FqEwh4L9H1QBHp2NKeKN6EE9VBnrquFCgTS9iTExd0BG7VBnkU4FhE/cwz55Xx/fbm4IXSnfZUQSkcd7Zs0pURI25OXOrZc3G2/pQATJPqxiHV0PJm4/35UHwAAAJS6uMisAwAAAFA8gTYFAAAAIIT8TkFE3MLY I5miPc3g3Bvy37tK/RrIdnI8T5lNN7bG0/juW9 2yrEONbC5HuO2YLsA8 TqvPnX/r35AstHgAgV0K fRDxwii/3JavV3lcYXJsS0xbbuo GHIjYpqA3MrpOVajdTmtviFivwed13MZACba JQUTKhS7T4YIBesD6nUJL hDgCTWahXEj2705TFiamiRu8PK7meJrVlalv71UjFsT5Xd6FpXWTyeO/uI93df9a29vh366nhjz3Y20l9KcoUBsVvn5KsdWTuotb52lYyCBnj2lrOuI e29IF30dreWccc1xNTFekajtF1a2t4RgbZZpfbTsZ3CDzi2mZN0zk6EvCuR3vc0XQ4sfZPbJaPlAa08Md5JzwStMAEEp7e0ciOO uGsN18ehcJr3rVG15R3eXAbvIdAynry9cV5LudfmFwbRPOmu 9G427UG1v65wWpzbcMa1th7jPhq25WBtI1A8J5dPH68vPz5dkVrLFFW3tno8ZZSpe3H3/5nmzxSX2r5J vxe05k7LKn1p5/jwc4jR/x7xpcrLGKe9H0GgDCy 3hRlC4eeRlT16m 3V0ausgMI2hXkslv0ru7UfXppjNIV8eS1rWlaX NXeoGiGvTPvrGra5YuyIV4TZ2R uOc/9tj0u3tl7H2ER1mmPqXjxNhvmjdetqqIbzOlc4fjJ1j2xMY4ZjYzwngqRpAAiqAL9TkMPuQtME6EqSiyNz0tVvUB77Ky6GmbtwNvHbx2zjNsDyBdEVaRF0a5vVMc5G2LgUZCbDo8vp8TxXjPGVz sFQOnJ7jsFUbp45GVMXacG7u4yOtkjll9XklG6 vXbJz8Z9terS90gcZ3aR62nx2zjNvDy49UVqVtxdmub3k23B9/uxT3ktDvyHtnltGdPfqZzheMni/PBL10E62ba3b4CAIIKWVLg7qoxSpeSYhlj16nW sQGrPXxL MjVMguPrlI0q8ryUhd/frtkx/D/iaLZNO71A0U1/JpnfdxhTY9StzqTMsXSlekRdatrdcx1huFOmTuXtwpm 7ImVYkL3sGNPSwZjxXRPxkcT54HhufcyKr4wAADjFuaLhy5f1qsDSgW8/Jhp8Mi79b20mbLsUTP7r BigOJfCdAhcukkS3nlBw0D0yAEy8Euo6Wb3nzEWS6NYTCk4dukcGgAkXa /oSKy8v7SqDwAAACBdCZUUAAAAgB9kCgAAAEAK2UsiAAAATFYF EVDAAAAmAjZfdEQAAAAJg2UFAAAAIAUR0EBAAAAMLx9AAAAABIyBQAAACAhUwAAAAASvlMAAAAAEt4 AAAAAAnfKQAAAAAJJQUAAAAgxdrb2xMLFixQgwAAAFCqYv8hMgV/tnSpGgQAAIBSFUftAQAAADB85hgAAACkeAwtDQEAAEBA9QEAAABIqD4AAAAAKU74ehEAAAAI KIhAAAASPiiIQAAAEjyi4ZL8fEiAIBQzl68TH/ZNUKv/up3dPHdK2osBFFfeS1t/ wMumX6FDXG3/vvv08XLlyg3/72t3TlCuI6jOuuu47KysroqquuUmP8IVMAABASZwju/O45aq79fVpfU0YzpsbVFMhkTGSgDpwco0d/dJ5 /PCHM2YMOEPwxhtv0Ic 9CG64YYbKB5HXAfFGaiRkRE6d 4c3XzzzYEyBnj7AAAgpM1Hxmjr4hvpa3ffgAxBSBxfG0RGakNtmSxpyYRvajfddBPdeOONyBCExPHFGSn cUlLEPhOAQBASF3979AX509XQxAFZwpePfc7NWR26dIlmjFjhhqCKDhTwFUvQaCkAAAgApQQZGfG1Cl08b1g7QOmTAnW9gC8cfwFbYtR2CUFh5tlDtH6NdNhNTp3DlPzjKW0Z1gNZmN4Dy1NriuH6wUAABgnhfudAr7JriTqGBujMf6dnEeDuc8VBBDwBj9nLR0aO0Rr56hhAABfz9Ia8QTHT3H2b9GuITVNGNpFi6YsIn0U5MsQ7VqkHYtFu8SY8cLpoHCOc F p2DoFL14xzwqV4N80127RP0PADApLKSd/Zfp8mX dVH1xrk0Zc2z1qTy9fTC5RdoffIiCHkhM19zqW LfRzE7wBRlzoMpSarSrGBgQE6ePCgfGXEC4/n6f39/WpMCEvq6aEXN9Mar0d0WVTvUa1gGq/T5lm6Z1CNVNKW51KClfQEvUib54txzdYaDzfb86TGmUsUhmnP0tT8ydkBAByW0d7 nbRwf6d4doTxMUS7GjdSdddl2rtMjWIiQ7ZeHy4hWWUKKioqaNq0afT9738/LWPAwzyep1dWVqqxYSyhlrGTdO/T8103U3Hznf803XtSVSt0EO2Qd2LTeB3Ps5mqOqx59tLT4oZv81q XIShgx6iO2g7j2 xiiqWtKh5eNoTO/yrFg7vos1VHWr MVKrAABIV15PDQv3U6fMFTiLlZ9doxVv26UJTD7pWuMX7dqlLaOW37UmuVx69URqnalVOovSk Md86 ZHBmXoS5qP7GKVvhkALzjPUPcFnEcZpUpiMVi9LnPfY6mT5/uyBjYGQIez9N5vmjm0NpD4mZ6cjv1rVQZg FB6rOf3Pnpe6V4jj8lDoZpvI7nuWM7rVc35jlrN4kbvhJkeVuyASSXImRQPo/ueGIlLfXNOQAA Fu2N1XNsGr/ttSNf671pMvTDlA77Zdz207Qxr4V1nJdq jExh3qRuRc7nL/TuqtV5mJZ3fQxuoutS37CZrnb6cGu6qji2ib4yZYxBZWkd9jq3e8M1PccoZgLrU39KvliisOs36nxp0x4Hchc5Mh0MxZS3u330FPdNnFBQ lGiDyL/n4bRofVIDlHQ0gT5IIlj/ZAJFLJdbIjITM2AAAGC2kKq 71LP2U2l96sY/1E 9C3fSJvWkW75 C62y/lUW0k574rIVYlov9fN9iJcTQ8kn5PL1tGXVCeobEP9XVtHC/fWuUgWeX9wE56qn3Pr9dELOPAmc6CPfPfGKd8kUt1bpwxZ3Y5AiicOcvGirZwwee yx3GQIDu/RiuWH6YdPv0h3zBORPKeCqsTzeVrVgGm8jud5cTPtUjfm4T07Uk/6QZZnegPI4R SCFYgc9YeopMiB9E3iBIDADCQN5RqmutuXMjFzvVEXfLJs592LlTj80E2cORSh0Z580pVK6xS21c/RyV8kXJU13jIebwXfhzmJFPA7IzBAw88kJsSgiUVdMouyp8xX9bLH5Lv y2hlpPbiTZbbQ3kTz5 m8brxDwdD9ETK63pa jeVPWBz3rrH9IaGi5ZT9tpM83n6WtOUVWmkgLtWwvzN1fRJryzCACe7CL9vZR2qxjooxN2MbfMOMix4qY2l6pPbKQd6qY2tGub62nWgJcTcyZvhuLmt22/s269fP0L1C/ugr38 KvmnzRVBknltH7LKtpfr2d BBEfu3jYFO9 VEYjLa6KJA5z p0Czghwo8KsMwQSNzQ0FOWrIvm0aabxuiUtyemH1q4V29C LWBYPtmwUA6rdg48fKiFWg7Zy3N4Pf7Xtjc21iKmAADYtOLkKduoqt/VCt62bBPtpI00l dr7KPq5BPrMtrbZd3UeB2N1CCeRYOw3nToVctNkXXdKjOSLC6fQnM3VqticGt EdjkNEdjx2K2bK9qU6H2i3 NRPUcGcZ49yMyGi o10vV qyoKo44RC JAAAhzfiXX9Dlf/q4GiogXNw9t4 2XPYobShAU/7 5zT2tx9VQ97OnDlDt956qxqCqF599VWaNWuWGjLLWfUBAABMrGd3bEwVdwNEgEwBAEBI06fGaezdYB3M5Jfzffj6/auo64X1qS/BFrCxdy r//xx97/cKA iCxN/yBQAAIR0642/R63HRtTQROL6a601e5FUG7ADL1 k spr1ZDZ1VdfTRcuXFBDEMXo6Chdd911asgfMgUAACF9s34mtR7/tfiNFEiJQfHg Hr0yHl69LnztP2z09VYsxtuuEFmCviHEoNwOL7OnTsnf2VlZWqsPzQ0BACI4OzF92lz1y oq2 UqGC7my0806dOoVs/ kH65n0fo1umX6XG uOv5L7us0MjIiohpxHRRXKfF3g7iB4VVXBYtrZAoAAABAilNOvikAAAAAxS6OLAEAAACwOH998L333lODAAAAUKriU6deS2 99ZYaBAAAgFIlMgVT6eLFi2oQAAAASlV82rRp8lWPS5cuqVEAAABQiuLXXHMNzZxZRq 99poaBQAAAKUoHo/HaMaM6bKk4OTJk/T222 rSQAAAFAK3nzzTfr6179OsVdeeSVhfzfb7vefv370wQ9 UH4JidscAAAAwOTCX4g8ffo0DQ8PU2dnJ50/f57 H7ZGmL9AcslaAAAAAElFTkSuQmCC[/IMG]

Any tips on what to do?

---

### Post by Morbius1 on 2023-05-14
Just based on what you posted you are missing a step on the Ubuntu server.

Unlike Windows where there is one user that represents the local login user and the network user in Linux there are two - one local and one samba.

You need to add kekke to the samba password database:
```
sudo smbpasswd -a kekke
```

---

### Post by kekkegg on 2023-05-14
Ive already done that :), followed this guide: 

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

The Ubuntu machine is not setup as an server. Just regular os :)

---

### Post by Morbius1 on 2023-05-14
If you installed samba and started the smbd daemon you are running a server ... with a desktop.

Does kekke have permissions on the folders being shared?

```
ls -al /media/kekke
```

---

### Post by kekkegg on 2023-05-14
No, I think that is the problem, kekke dont have permissions. 

what will the ls- al command do? :)

---

### Post by Morbius1 on 2023-05-14
It will list the permissions of the /media/kekke/plot1 and /media/kekke/plot2 folders.

Of course the permissions depend on whether something is mounted to them or not. A mount always replaces the mount points permissions with it's own.

And I'm assuming they are mount points.

If you run this command is something mounted to them:
```
mount | grep /media/kekke
```

---

### Post by kekkegg on 2023-05-14
Ok, ill check it out. 

How can I give myself permission if its root that owns it?

---

### Post by Morbius1 on 2023-05-15
Insufficient information provided to answer the question.

Please post the output of the following commands:

```
sudo blkid -c /dev/null -o list
```
```
cat /etc/fstab
```
```
ls -al /media/kekkel
```

---

### Post by kekkegg on 2023-05-15
Thanks for helping btw!

Ok, ok the first command ill get

**sudo blkid -c /dev/null -o list**


device     fs_type label    mount point    UUID


**cat /etc/fstab**

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=8133b2d6-ba96-4012-83b9-b2e93884974a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=32AB-C9D5  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-uuid/da6aa6a7-6d35-4866-919c-1bc21149b02c /mnt/plot2 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot2 0 0
/dev/disk/by-uuid/37edcd2b-81f6-47f7-bf5f-8ad4e3518f4f /mnt/plot1 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot1 0 0
/dev/disk/by-uuid/6ffb3790-669f-49d8-b19d-832e5a4b32fb /mnt/plot2 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot2 0 0
/dev/disk/by-uuid/8cc763ef-d3b4-43aa-bd42-1911efac9175 /mnt/plot2 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot2 0 0
/dev/disk/by-uuid/c651f66f-3794-47df-b8d5-5ab0e3474511 /mnt/plot2 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot2 0 0
/dev/disk/by-uuid/bfeeae90-c0df-4567-8020-66a29bc23090 /mnt/plot2 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot2 0 0
/dev/disk/by-uuid/8239f95a-7ffd-4ea2-945f-766ac1b0512e /mnt/plot2 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot2 0 0
/dev/disk/by-uuid/2754f872-fd67-4a62-8c8f-35a2e5cc585e /mnt/plot3 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=plot3 0 0

**ls -al /media/kekke**



total 72
drwxr-x---+ 11 root  root  4096 mai   14 17:25 .
drwxr-xr-x   3 root  root  4096 mai    5 21:12 ..
drwxr-xr-x   4 root  root  4096 mai   13 09:26 plot1
drwxr-xr-x   4 root  root  4096 mai   14 17:26 plot4
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots1
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots2
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots3
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots4
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots5
drwxrwxrwx   1 kekke kekke 4096 mai    3 14:12 Plots6

Im currently changing from the NTFS to the EXT4 file system on my drives. The 4 top ones are the one I have changed to EXT4 file system, the other ones are NTFS disks from my old Windows PC

---

### Post by Morbius1 on 2023-05-15
> [plot2]
path = /media/kekke/plot2/
valid users = kekke
read only = no


I can view the folders on my windows computer, but when ill try to open them ill get this error message:

Windows cannot access \\10.10.x.x\plot2

Windows cannot access \\10.10.x.x\plot2 because there is no /media/kekke/plot2 on the server.

Now I am forced to do my own web searches to find out under what conditions it is even possible for the blkid command to produce no output.

---

### Post by ActionParsnip on 2023-05-16
> **Morbius1 said:**
> Windows cannot access \\10.10.x.x\plot2 because there is no /media/kekke/plot2 on the server.

Now I am forced to do my own web searches to find out under what conditions it is even possible for the blkid command to produce no output.

Yeah, the shared points you set in the file don't match the file system

---

