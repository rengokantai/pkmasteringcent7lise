#### pkmasteringcent7lise
- cp1

enable user quota
```
vi /etc/default/grub
```
Add the following to ```GRUB_CMDLINE_LINUX```
```
rootflags=usrquota,grpquota
```

The grub file will compile to /boot/grub2/grub.cfg, so we can backup the original file.
```
cp /boot/grub2/grub.cfg /boot/grub2/grub.cfg.bak
```
rebuild:
```
grub2-mkconfig -o /boot/grub2/grub.cfg
```
install quota:
```
yum install -y quota
```
check current quota:
```
repquota -as
```

Edit quota:
```
edquota -u username
edquota -g grpname
```

To remount /var:
```
mount -o remount /var
```
To enable quota:
```
quotacheck -avugm
quotaon -avug
```

password aging
lock a user
```
usermod -L user
```
password age
```
chage -d 0 user
```
assign password
```
usermod -p pass user
```
password aging conf is ```/etc/login.defs```  
password complexities is```etc/pam.d/system-auth```  
Add ```ucredit=-2 lcredit=-2 dcredit=-2 ocredit-=2``` in password requisite  
o=symbol d=digit l=lcase u=ucase, at least 2.  

remember=x(x past password should be denied)  


/etc/sudoers = visudo

set default editor:
```
export EDITOR=/usr/bin/nano
```
Then source the file:
```
. ~/.bashrc
```

