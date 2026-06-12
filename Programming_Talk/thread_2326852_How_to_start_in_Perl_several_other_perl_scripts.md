---
title: "How to start in Perl several other perl scripts?"
date: 2016-06-05
forum: Programming Talk
---

### Post by Roland_Msl on 2016-06-05
Just doing my last step at the Exodus from Windows: Rewriting my old MSHTA dependent software to client server.

In the Windows version:
MSIE was used as GUI, *.hta applications, something like html where 
<script language=PerlScript>
....here goes all the Perl code
</script>

In the new client server version:
Google Chrome as GUI.
The perl script service.pl opens a port,
starts the browser with [http://localhost:10500/here-some-parameters](http://localhost:10500/here-some-parameters)
The perl script is called on port 10500 and delivers the html page.

There is a list of domains, and each domain has links on the page
* to call the CMS for this domain
* to view the local version of the domain

View the local version works fine.
The page javascript calls server.pl with

function view(site)
{
    var xhttp = new XMLHttpRequest();
    xhttp.open('GET', url+'?do=view&site='+site, true);
    xhttp.send();
}

and in server.pl

    if ( $do eq 'view' )
    {
        system ( $wm2::browser, "$path::internet/$site/index.htm" );
        return;
    }

For each click, a new window opens, showing the localc stored start page of the wanted domain.


The problem is opening the CMS for a domain.
The javascript

function wsc(i)
{
    var xhttp = new XMLHttpRequest();
    xhttp.open('GET', url+'?do=WSC&index='+i, true);
    xhttp.send();
}

and in server.pl

    if ( $do eq 'WSC' )
    {
        my $i    = $wm2::data_hash { 'index'};
        my $site    = $site::tab [ $i ];
        my $port    = 10510 + $i;              

        system ( "perl", "$path::internet/cgi.pege.org/cgi-bin/server.pl", "task=WSC", "site=$site", "port=$port" );
        return;    
    }

A new windows opens with the CMS for the wanted domain,
but after this, no click creates an reaction, the browser window with the domain list is dead.

So I think, calling the browser, the browser returns controll to server.pl after opening a new browser window
but calling perl, the controll is not returned to server.pl, so server.pl can not react any more.

In windows, 
        system ( "start", "perl.exe", "$path::internet/cgi.pege.org/cgi-bin/server.pl", "task=WSC", "site=$site", "port=$port" );
helped,
but I can not find out gow to do it here

---

### Post by Roland_Msl on 2016-06-06
I found a solution

sub call_shell
{
 	my ( $shell, @param_tab ) = @_;
  
  	if ( open ( MYSHELL, ">$shell" ) )
   	{
	  	print "call_shell * create $shell\n";
 		print MYSHELL "$path::internet/cgi.pege.org/cgi-bin/server.pl";
 		my $param;
 		foreach $param ( @param_tab)
 		{
			print MYSHELL  " $param";
 		}
		print MYSHELL " &\n";
		close ( MYSHELL );
		chmod 0755, $shell;
		system ( $shell ) ;
   	}
	else
 	{
	  	print "call_shell * can not open $shell\n\n";
	}
 }

But I think there should be a more elegant way, than writing a batch file with "&" at the end of the line.

---

