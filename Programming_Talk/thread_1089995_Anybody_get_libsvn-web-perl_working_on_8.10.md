---
title: "Anybody get libsvn-web-perl working on 8.10?"
date: 2009-03-07
forum: Programming Talk
---

### Post by sorakiu on 2009-03-07
I like being able to browse my own svn repo using libsvn-web-perl but I can't remember how to get it working.

My repository is in my homedirectory : ~/svn

So I tried creating a config.yaml in my home directory with:
  repos:
    my_local_repo: 'file:///home/sorakiu/svn'

and then i tried running svnweb-server

it loaded but when i tried to browse to it, i got:
HTTP::Server::Simple: You can connect to your server at [http://localhost:8080/](http://localhost:8080/)
[Sat Mar  7 18:41:02 2009] svnweb-server: Died at /usr/share/perl5/YAML/Loader.pm line 671.

and the web browser was blank.

671 is:
```

            $self->lines->[0] =~ /^( *)\S/ or die;

```

more context:
```

    # Determine the offset for a new collection level
    elsif ($type == COLLECTION and 
           $self->preface =~ /^(\s*(\!\S*|\&\S+))*\s*$/) {
        $self->_parse_throwaway_comments();
        if ($self->eos) {
            $self->offset->[$level+1] = $offset + 1;
            return;
        }
        else {
            $self->lines->[0] =~ /^( *)\S/ or die;
            if (length($1) > $offset) {
                $self->offset->[$level+1] = length($1);
            }
            else {
                $self->offset->[$level+1] = $offset + 1;
            }
        }
        $offset = $self->offset->[++$level];
    }

```

I feel like I'm missing something obvious.  Can someone tell me what it is?

-dave

---

