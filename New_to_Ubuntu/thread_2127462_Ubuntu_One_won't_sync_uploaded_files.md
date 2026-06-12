---
title: "Ubuntu One won't sync uploaded files"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by Frozen Forest on 2013-03-20
I got two computers connected to the same Ubuntu One account, one of these computers have uploaded some files to the ubuntu one server, they are available from the web interface, problem is that these files never get synced to the other computer, this one is simply stuck. u1sdtool --waiting give the following output (removed id), I'm guessing that this might be the cause
```

u1sdtool --waiting
  MakeDir(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='Name', parent_id='marker:0000-0000-000')
  MakeFile(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='Name', parent_id='marker:0000-0000-000')
  MakeDir(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='/some/path', parent_id='marker:0000-0000-000')
  MakeDir(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='/some/path', parent_id='marker:0000-0000-000')
  MakeFile(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='/some/path', parent_id='marker:0000-0000-0000')
  MakeFile(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='/some/path', parent_id='marker:0000-0000-0000')
  MakeFile(running=False, share_id='0000-0000', path='/some/path', marker='marker:ff0000', name='/some/path', parent_id='marker:0000-0000-0000')
  Upload(running=False, share_id='0000-0000', node_id='marker:ff0000', path='/some/path', crc32='269624', hash='sha1:527b1', previous_hash='', size='35791', upload_id='None')
  Upload(running=False, share_id='0000-0000', node_id='marker:ff0000', path='/some/path', crc32='577569', hash='sha1:d372b1e', previous_hash='', size='958', upload_id='None')
  Upload(running=False, share_id='0000-0000', node_id='marker:ff0000', path='/some/path', crc32='3761', hash='sha1:80834', previous_hash='', size='1810', upload_id='None')
  Upload(running=False, share_id='0000-0000', node_id='marker:ff0000', path='/some/path', crc32='245889', hash='sha1:4b5c', previous_hash='', size='1723', upload_id='None')



```

---

