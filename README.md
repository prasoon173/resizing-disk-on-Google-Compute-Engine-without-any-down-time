# resizing-disk-on-Google-Compute-Engine-without-any-down-time
Here, I have resized the boot disk of Google Compute Engine without any downtime


1. Go go Disk section of Compute or use cli ( gcloud compute disks resize example-disk --size 250 ) 
2. click on the disk which you want to resize.
3. on right sied, click on threee doted edit button and click edit. 
4. enter the new disk size which you want it to be and save. Now, you could see that it will show you the updated disk size here but on VM if you do $df -h , it will still show you last disk size only. 

Hence, you will need to resize it using ssh to vm. 

$ sudo apt install -y cloud-utils         
$ sudo apt install -y cloud-guest-utils  
$ sudo growpart /dev/sda 1
$ sudo resize2fs /dev/sda1

prasoon_p@sql-demo-host:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            485M     0  485M   0% /dev
tmpfs            99M   11M   89M  11% /run
/dev/sda1        15G  1.8G   13G  13% /
tmpfs           494M     0  494M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           494M     0  494M   0% /sys/fs/cgroup
/dev/sda15      124M  5.7M  119M   5% /boot/efi
tmpfs            99M     0   99M   0% /run/user/1001
