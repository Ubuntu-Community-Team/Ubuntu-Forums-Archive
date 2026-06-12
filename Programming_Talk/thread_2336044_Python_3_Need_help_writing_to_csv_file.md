---
title: "Python 3 Need help writing to csv file"
date: 2016-09-03
forum: Programming Talk
---

### Post by lance bermudez on 2016-09-03
```

import csv

stud1 = {}
stud2 = {}

with open('fsreport-FriSep022016.csv') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        sha = row['SHA512']
        files = row['File']
        paths = row['Path']
        stud1[sha] = files, paths

with open('fsreport-SatSep32016.csv') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        sha = row['SHA512']
        files = row['File'] 
        paths = row['Path']
        stud2[sha] = files, paths

# stud1 not in stud2
for key in stud1:
    if not key in stud2:
        print('')
        print('key  in oldest Dit1 not found in Newest Dit2')
        print(key, '\n')
        turn = key
        if turn in stud1:
            files, paths = stud1[turn]
            print(turn, sha, files, paths)

# stud2 not in stud1
for key in stud2:
    if not key in stud1 or stud2[key] != stud1[key]:
        print('')
        print('key in Newest Dit2 not found in oldes Dit1')
        print('OR key in Newest Dit2 != oldes dit1')
        #print(key, '\n')
        turn = key
        if turn in stud2:
            files, paths = stud2[turn]
            print(turn, sha, files, paths)

```

How do i save the print outs to a two csv files. 
first file # stud1 not in stud2
first file key  in oldest Dit1 not found in Newest Dit2

second file # stud2 not in stud1
second file key in Newest Dit2 not found in oldes Dit1
second file OR key in Newest Dit2 != oldes dit1

---

### Post by nargaroth_reg on 2016-09-04
I'm not sure I understand exactly what you're trying to save in the csv files, but for the first part I think something like this should work, using the writer method from the csv module.
```

with open('dest_file_name.csv', 'w') as csvfile:
    wr = csv.writer(csvfile, delimiter=',', lineterminator='\n')
    for key in stud1:
        if not key in stud2:
            wr.writerow(['{} in oldest Dit1 not found in Newest Dit2'.format(key)])

```
more info can be found here: [https://docs.python.org/3.5/library/csv.html#csv.writer](https://docs.python.org/3.5/library/csv.html#csv.writer)

---

### Post by lance bermudez on 2016-09-04
Sorry for not making my self more clear and thank you for the help. With your help I at least have the hash of the file but how do I get the rest of the output?

How do i save the print outs to a two csv files.
first file # stud1 not in stud2
first file key in oldest Dit1 not found in Newest Dit2
the out put below is what I get that I want to save to the csv file
if turn in stud2:
            files, paths = stud2[turn]
            print(turn, files, paths) # this out put to csv file
```

key  in oldest Dit1 not found in Newest Dit2
9DC676D6F64B7C9BB8D5601A29E8A6FA164472C1C48E9AE2D0B1274F975505BA5B0DAEEB6EB8457D7F427A15581E59A1A6D639F89B9468D1ABA8BC335DED5252 scans06.jpg~ /home/lance/acer/New/scans06.jpg~

key  in oldest Dit1 not found in Newest Dit2
2132EB33389196068F42AA0B80885E838C85BDC18BBD24C1A5B71018987B3359253B65C2987CBA62843665590A6E74F39AC190C16FAD0767D30CBDC393EC86E7 scans~523.jpg~ /home/lance/acer/New/scans~523.jpg~

key  in oldest Dit1 not found in Newest Dit2
0ED83C1245A5C4ACD6DE513C86B0B57E5E428319175D59F887ACA2101DFF9ABE9489EDEE98A3860B872556F58C08CFD97CBF6CC41B76DC0DDC476C16A13471E8 Scans_493.jpg~ /home/lance/acer/New/Scans_493.jpg~

key  in oldest Dit1 not found in Newest Dit2
7FF145391690BB34A1B16CC52DC385F7C04129B7CA30C25A12E092BD7F48284EE40FBCC8A8B4E4D9C77B1BEDCA4911711CEDA3C23E152F848ABFA73E199E77EA mozxtzjwZ21rdpovjo1_500.jpg~ /home/lance/acer/New/mozxtzjwZ21rdpovjo1_500.jpg~

key  in oldest Dit1 not found in Newest Dit2
A117E2E08C40A555C342123B4BEAD9E47F4909208EC74DC171076B6E852E58BC3B1E83BDA438CA867743AC05B43ED747319E85FE831A98C765CBB796469B7BBC Scans_488.jpg~ /home/lance/acer/New/Scans_488.jpg~

key  in oldest Dit1 not found in Newest Dit2
0C00167FA8F5A6F2BFC8764F6A41DBA9031F0A60086FC0F5E8E6DC0E0C8A4BD933487DAF8337DCB19EE27EAC3BE30479A8CBE4B5402F41CCDE4F4A38AD002AD1 comics /home/lance/acer/New/comics

```

second file # stud2 not in stud1
second file key in Newest Dit2 not found in oldes Dit1
second file OR key in Newest Dit2 != oldes dit1 
the out put below is what I get that I want to save to the csv file
if turn in stud2:
            files, paths = stud2[turn]
            print(turn, files, paths) # out put to save to csv file
```

key in Newest Dit2 not found in oldes Dit1
OR key in Newest Dit2 != oldes dit1
CF83E1357EEFB8BDF1542850D66D8007D620E4050B5715DC83F4A921D36CE9CE47D0D13C5D85F2B0FF8318D2877EEC2F63B931BD47417A81A538327AF927DA3E ytubedl-2016.07.30.tar.gz /home/lance/acer/New/ytubedl-2016.07.30.tar.gz

key in Newest Dit2 not found in oldes Dit1
OR key in Newest Dit2 != oldes dit1
F8D84B7D8DF70604DBC5B186DF6E959714E52669FC74932B1C2C78703AECC2F09B723CF60D196A7BCA28AE1D25A999D00C937498B0F86FCE853868AE7D36D625 2.txt /home/lance/acer/New/1/2.txt

key in Newest Dit2 not found in oldes Dit1
OR key in Newest Dit2 != oldes dit1
A37C5CC24B005D2ACC71D193A3073A089BDF35B6CD0EC5F93444A263A9BB49A24CDC2279F1C5822744FCF5E304C535B0DCB4AB630FBD3EBDDB4C82E82F056DEA Efile.asc /home/lance/acer/New/Efile.asc

key in Newest Dit2 not found in oldes Dit1
OR key in Newest Dit2 != oldes dit1
1B8CE740745374246ED5A02181D1D8A7C1F40AB036AE9B2E712698604B11C2066875064C2C5D5FAF8516B14035B4C288B6EB46926730D8332A68248BB6855128 Efile.gpg /home/lance/acer/New/Efile.gpg

key in Newest Dit2 not found in oldes Dit1
OR key in Newest Dit2 != oldes dit1
B3D26EBB9E56ECD91E77FD438C30C8651914B1E812CF519172D2DD86C7C52B0289EE2F6E0FBC86D0B41CB14D623778F23FE08DAB4D2E78057A59B765D488A627 3.txt /home/lance/acer/New/1/3.txt

```

---

