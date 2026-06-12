---
title: "Perl Tk - Radiobuttons()"
date: 2010-02-01
forum: Programming Talk
---

### Post by iMisspell on 2010-02-01
Before hitting Perl forums, thought i would ask here.

Heres the scoop.
I have a sql-table; id, type, file and path ('type' is used as a "flag" to determine if the file is an 'Install' file or an 'Update' file (which is where the Radio buttons come in)).

Im dynamically create a bunch of Radio-buttons with the code below.
What i would like is to have rows of "install/update" buttons with a label to the right of the two RadioButtons (which ive been successful in doing), but im having a problem with toggling the buttons. 
Ive tried a bunch of things, placing the r-buttons in frames, not in frames, changing the RadioButtons 'value' and 'variable'. No matter what ive tried, i can not get the buttons to toggle correctly and display correclty. 
When toggling, ether *all* the 'install' buttons become selected when only selecting one, or only a single buttons is selected and not toggling anything, or selecting 'install' on a row will select both buttons on that row, but never toggling each row correctly.
When the buttons are first displayed, none of them are 'selected', all buttons are 'deselected'.

All the arrays are being filled correctly, used 'print' to double check. The r-button '-command =>' works correctly and sets the correct information in the sub it calls.

Heres the code
[PHP]

sub setExensionFilesChk{
	
	my $index1 = $_[0] || return ;
	$index1 = ($index1 -1);
	my $extNameIs = "$extensionNames[$index1][0]";
	#print "* $extNameIs *\n";
	
	@extensionFiles=();
	@extensionFileBothInstall=();
	my $q = $db->query("SELECT filelist_id, filelist_type,filelist_path,filelist_file   FROM filelist WHERE filelist_extension = '$extNameIs'");
	while (my $ref = $q->fetchrow_hashref() ) {
		#print "$$ref{'filelist_file'}\n";
		push @extensionFiles, [ $$ref{'filelist_id'}, $$ref{'filelist_type'}, $$ref{'filelist_path'}, $$ref{'filelist_file'} ];
		push @extensionFileBothInstall, [ $$ref{'filelist_id'}, $$ref{'filelist_type'} ];
	}
	
	$extFileFrame->destroy if $extFileFrame;
	
	$extFileFrame = $fileListPane -> Frame();
	$extFileFrame->configure( -width=>500, -height=>400 );
	$extFileFrame -> grid(-row=>1,-column=>1,-columnspan=>3,-sticky=>"nw");
	
	my $names;
	my $i = 0;
	my $rdb;
	
	for $names ( @extensionFiles ) {
		$i++;
		
		if("@$names[1]" eq "both"){
			
			#print "@$names[3]\n";
			
			my $FileFrame = $extFileFrame -> Frame();
			$FileFrame -> grid(-row=>($i + 1),-column=>1,-columnspan=>3,-sticky=>"nw");
			
			$rdb = $FileFrame -> Radiobutton(-text=>"Both", -value=>"@$names[0]", -variable=>"@$names[1]", -command => [ \&setFileBothInstall, "@$names[0]", 'both' ]);
			$rdb -> select();
			$rdb -> grid(-row=>(1),-column=>0, -sticky=>"w");
			
			$rdb = $FileFrame -> Radiobutton(-text=>"Install", -value=>"@$names[0]", -variable=>"@$names[1]", -command => [ \&setFileBothInstall, "@$names[0]", 'install' ]);
			$rdb -> deselect();
			$rdb -> grid(-row=>(1),-column=>1, -sticky=>"w");
			
			my $lab = $FileFrame -> Label(-text=>" - @$names[2]@$names[3]");
			$lab -> grid(-row=>(1),-column=>2, -sticky=>"w");
			
		} else {
			
		}
		
	}
	
	my $lbl_extName = $extFileFrame -> Label(-text=>"($i) Extension Files:");
	$lbl_extName -> grid(-row=>1,-column=>0,-columnspan=>3);
	
	$extensionsFilesWindow->update;
	
}

[/PHP]

And an image to get a visual, the five r-buttons on the left are used to call the sub posted above which will display the files from the sql-table and display them to the list on the right, which is where the problem is.

Thanks for any help with this...

_

---

### Post by iMisspell on 2010-02-26
With a snowy weekend here, too tired to do anything but play on the computer, bumping this for a fresh pair of eyes....

---

### Post by iMisspell on 2010-02-27
Thanks to the help of a member over at perlmonks.org, the following code works.
Heres a link to the thread to see the process...
[http://perlmonks.org/index.pl?node_id=825618](http://perlmonks.org/index.pl?node_id=825618)

Working code...
[php]sub setExensionFilesChk{
	
	my $extensionNameIndex = $_[0] || return ;
	$extensionNameIndex = ($extensionNameIndex -1);
	my $extNameIs = "$extensionNames[$extensionNameIndex][0]";
	
	$extFileFrame->destroy if $extFileFrame;
	
	$extFileFrame = $fileListPane -> Frame();
	$extFileFrame->configure( -width=>575, -height=>400 );
	$extFileFrame -> grid(-row=>1,-column=>1,-columnspan=>4,-sticky=>"nw");
	
	my $rowIndex = 1; # start with 1 so that 'row' 0 is empty and resurved for the "total count label"
	my ($rdb1,$rdb2,$but,$lab);
	
	my @tmpFiles = getExtensionsFiles("$extNameIs");
	for my $names ( @tmpFiles ) {
		$rowIndex++;
		
		# add 'Delete' button...
		$but = $extFileFrame -> Button(-text=>"x", -command => [ \&setFileType_BothOrInstall_Or_Delete, "@$names[0]", 'delete', \$extensionNameIndex ]);
		$but -> grid(-row=>$rowIndex,-column=>0, -sticky=>"w");
		
		# Radio Buttons...
		$rdb1 = $extFileFrame -> Radiobutton(-text=>"Both", -value=>"both_@$names[0]", -variable=>"both_@$names[0]", -command => [ \&setFileType_BothOrInstall_Or_Delete, "@$names[0]", 'both' ]);
		$rdb1 -> grid(-row=>($rowIndex),-column=>1, -sticky=>"w");
		
		$rdb2 = $extFileFrame -> Radiobutton(-text=>"Install", -value=>"install_@$names[0]", -variable=>"both_@$names[0]", -command => [ \&setFileType_BothOrInstall_Or_Delete, "@$names[0]", 'install' ]);
		$rdb2 -> grid(-row=>($rowIndex),-column=>2, -sticky=>"w");
				
		if("@$names[1]" eq "both"){
			$rdb1 -> select();
			$rdb2 -> deselect();
		} else {
			$rdb1 -> deselect();
			$rdb2 -> select();
		}
		
		# label with file path and file name...
		$lab = $extFileFrame -> Label(-text=>" - @$names[2]@$names[3]");
		$lab -> grid(-row=>($rowIndex),-column=>3, -sticky=>"w");
		
	}
	@tmpFiles=();
	
	my $lbl_extCount = $extFileFrame -> Label(-text=>"($rowIndex) Extension Files:");
	$lbl_extCount -> grid(-row=>1,-column=>3,-columnspan=>1, -sticky=>"w");
	
	$extensionsFilesWindow->update;
	
}[/php]

---

