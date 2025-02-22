# Eman2-installation

* Installation from source file
Ref: https://blake.bcm.edu/emanwiki/EMAN2/Install/SourceInstall

* Machine and conda status
Ubuntu in WSL2 windows 11 / several conda env already set

* Pre-installation check up
  - $PATH has miniforge dir set
  - LD_LIBRARY_PATH is set
  - $PYTHONPATH is blank from
>conda deactivate

Setting LD library path wiping is risky as all important programs are running seamlessly &
MiniForge is already installed
* Configure and update conda
  - creating a silent conda env for eman2 => will need to activate conda env for using eman2
  - I will skip it, since conda is already deactivated and I don't want to change conda config at this point
(>conda config --set auto_activate_base False)
  - Switching auto update of conda env off (if it is not already off)
>conda config --set auto_update_conda False
  - Minforge is already isntalled, no need to isntall mamba, otherwise run the following 
>conda install mamba -c conda-forge
- Update base env of mamba to get the latest conda
>mamba update --all -n base
# Create new conda env
>mamba create -n eman2 eman-dev --only-deps -c cryoem -c conda-forge
  - Confirm you have OpenGL in the system
  - Install OpenGL
>sudo apt install mesa-utils
>glxinfo | grep "OpenGL version"
OpenGL version string: 4.6 (Compatibility Profile) Mesa 24.2.8-1ubuntu1~24.04.1

# Get EMAN code
- Set a directory for source code [EMAN2] & enter
>conda info --envs
>conda activate eman2

* OPENGL crisis
>sudo apt-get install cmake pkg-config
>
>sudo apt-get install mesa-utils libglu1-mesa-dev freeglut3-dev mesa-common-dev
>
>sudo apt-get install libglew-dev libglfw3-dev libglm-dev
>
>sudo apt-get install libao-dev libmpg123-dev

- instll openGL library
>apt install freeglut3-dev
- issue of missing xkbcommon library
>sudo apt install libwayland-dev libxkbcommon-dev xorg-dev

# Installation
>cd EMAN2

>git fetch --all --prune
>
>git checkout master
>
>git pull
>
>mkdir build
>
>cd build
>
>cmake <source-directory> -DENABLE_OPTIMIZE_MACHINE=ON
  - in case of error of not finding python, reboot & activate eman2 env
>make -j 8
>
>make install
>
>make install-sphire

https://blake.bcm.edu/emanwiki/EMAN2/Install/SourceInstall



