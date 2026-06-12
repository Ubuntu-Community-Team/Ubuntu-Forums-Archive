---
title: "RT and perl programmer's help wanted :D"
date: 2011-08-24
forum: Programming Talk
---

### Post by RRJ on 2011-08-24
Hello, dear community.

I ask You guys, for some Perl help :) Those, who have ever worked with RT (request tracker) would know, what am i talking about :)

there is a file for Self Serverice users (unprivileged) like
%rtroot/html/SelfService/Elements/MyRequests
the code is below:
```

<&| /Widgets/TitleBox, title =>  $title &>
<& /Elements/CollectionList, Title   => $title,
                         Format  => $Format,
                         Query   => $Query,
                         Order   => @Order,
                         OrderBy => @OrderBy,
                         BaseURL => $BaseURL,
                         GenericQueryArgs => $GenericQueryArgs,
                         AllowSorting => $AllowSorting,
                         Class   => 'RT::Tickets',
             Rows    => $Rows,
                         Page    => $Page &>
</&>

<%INIT>
my $id = $session{'CurrentUser'} -> id;
my $Query = "( "
    . join( ' OR ', map "$_.id = $id", @roles )
    . ")";
if ( @status ) {
    $Query .= " AND ( "
        . join( ' OR ', map "Status = '$_'", @status )
        . " )";
}
my $Format = RT->Config->Get('DefaultSelfServiceSearchResultFormat');

</%INIT>
<%ARGS>
$friendly_status => loc('open')
$title => loc("My [_1] tickets", $friendly_status)
@roles => ('Watcher')
@status => RT::Queue->ActiveStatusArray()
$BaseURL => undef
$Page => 1
$GenericQueryArgs => undef
$AllowSorting => 1
@Order => ('ASC')
@OrderBy => ('Created')
$Rows => 50
</%ARGS>

```

which by default shows only those tickets to unprivileged SelfService users, that are created only by themselves (the part about $id). I want to modify this script, so it would show those messages, that belong to this users's organization.
(there is somewhere an object Organizations or smth like that, as one can set it up for user during add procedure)
Can anyone help? i googled for 2 days already and nothing.

---

### Post by RRJ on 2011-08-24
oh, solved. found [this]("http://requesttracker.wikia.com/wiki/RichardF")

---

