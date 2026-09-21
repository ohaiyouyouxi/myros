# myros
## 第一步：先获取`root`权限
```
sudo su
```
## 第二步：准备软件源环境
```
apt update
apt install -y curl gnupg2 lsb-release software-properties-common
add-apt-repository universe
```
## 第三步：添加`ROS`软件源和签名
```
mkdir -p /etc/apt/keyrings
curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo tee /etc/apt/keyrings/ros.asc > /dev/null
echo "deb [signed-by=/etc/apt/keyrings/ros.asc] http://packages.ros.org/ros/ubuntu focal main" | sudo tee /etc/apt/sources.list.d/ros1.list
```
## 第四步：更新并安装完整桌面版
```
apt update
apt install -y ros-noetic-desktop-full
```
## 第五步：配置环境变量
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
## 第六步：再安装开发工具和`rosdep`
```
apt install -y python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
## 第七步：`ROS`初始化
```
rosdep init
rosdep update
```
## 最后一步：`ROS Master`测试
```
roscore
```
> 输出`started core service [/rosout]`则完美通过测试
## 小结
安装过程没有遇到问题。`wsl2`支持图形化，不必安装繁重的`vmware`。
