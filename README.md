# Debian9-AMD64-gcc-4.9

This is the .deb files from the Debian 8 repo for installing gcc-4.9 g++-4.9 and gcc-4.9-multilib
I had to link them on google drive as the file is 85 megs and to big for github.

https://drive.google.com/uc?export=download&confirm=bsgg&id=1F1nD3UR2BAj88uMKkf9hhi06hQVWS_0i

These files were extracted on Debian 9 AMD64 by adding the jessie archive to sources.list and running 

apt-rdepends gcc-4.9 g++-4.9 gcc-4.9-multilib  | awk '$1 ~ /^Depends:/{print $2}' | xargs apt-get download

This process looks up the dependencies for the requested program and downloads them in to the current 
directory you are in.

You can use wget to fetch the file to untar it and use dpkg -i *.deb to install.

Once you have gcc-4.9 installed you can install build-essential from Debian 9 this will give you both
gcc 4.9 and 6.x you can then use the following to select 4.9 as the default and build what ever programs
you need 4.9 to compile.

update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 20
update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.9 20

update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 30
update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-6 30

update-alternatives --set cc /usr/bin/gcc
update-alternatives --set c++ /usr/bin/g++

update-alternatives --config gcc
update-alternatives --config g++
