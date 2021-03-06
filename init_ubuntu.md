# init-Ubuntu
>   小插曲：连续两天每天换电脑然后在Ubuntu下重装软件配置环境，于是就琢磨着记录下来，供以后自己再换电脑时能够快速的知道需要安装哪些软件 [ps:有些安装步骤其实并不需要记录的，但为了避免以后脑子不好使所以还是不怕麻烦的记录下来]
### fcitx 
``` bash
* sudo add-apt-repository ppa:fcitx-team/nightly
* sudo apt-get update
* sudo apt-get -f install
* sudo apt-get install fcitx  
```
### 搜狗输入
```bash  
* [官方下载安装包](https://pinyin.sogou.com/linux/?r=pinyin)
* sudo dpkg -i sogou*
* sudo apt-get install -f
* system setting->language support->设置fcitx(若未安装需先行安装)  
```
### chrome
```bash 
* sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
* wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
* sudo apt-get update
* sudo apt-get install google-chrome-stable
```
##### chrome相关插件
[redux](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en-US), [react](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en-US), ~~Instant Translate(用过最好用的翻译插件)~~, [google translate](https://chrome.google.com/webstore/detail/google-translate/aapbdbdomjkkjkaonfhkkikfgjllcleb?hl=en-US), [Octotree](https://github.com/buunguyen/octotree), [GitHub-Dark](https://github.com/StylishThemes/GitHub-Dark), [stylish](https://github.com/stylish-userstyles/stylish)
### git
``` bahs
* sudo apt-get install git
```
### Node及Npm
```bash 
* [官方下载安装包](https://nodejs.org/en/download/)
* tar xvf node*tar.gz
* sudo mv node* /opt/node //个人有将包移到opt目录下的习惯，当然时非必须的。
*  cd node*/bin
*  ./node -v
*  sudo ln -s /opt/node/bin/node /usr/local/bin/node // 非必须但是很有必要的
*  sudo ln -s /opt/node/bin/npm /usr/local/bin/npm  
```
#### 或者   
```bash 
* wget https://nodejs.org/dist/v8.9.1/node-v8.9.1.tar.gz
* tar xvf node*.tar.gz 
* cd node*
* ./configure 
* make 
* make install 
* 移动位置创软连接,同上...
```
### curl
```bash
* sudo apt-get install curl
```
### yarn 
```bash
*  curl -o- -L https://yarnpkg.com/install.sh | bash
```
### nrm  
在公司因为要安装公司仓库的私有包，所以需要地址。回家没内网安装包需淘宝镜像又得改。[github](https://github.com/Pana/nrm)
```bash
npm config set registry https://registry.npm.taobao.org/
```
so,nrm就显得比较重要了。  
```bash
    sudo npm install -g nrm // 安装
    sudo ln -s /opt/node/bin/nrm /usr/local/bin/nrm  //软链接
    nrm add diyName http://your.company.registry/  // nrm ls看列表
    nrm use/del/test taobao
```
### subliem
```bash
* [官方下载安装包](https://www.sublimetext.com/3)
*  tar vxjf sub*
*  sudo ln -s /home/ksuser/Downloads/sub* /usr/local/bin/subl  
或者  
* sudo add-apt-repository ppa:webupd8team/sublime-text-3
* sudo apt-get update
* sudo apt-get install sublime-text-installer  
卸载  
* sudo apt-get remove sublime-text-installer
```
##### sublime相关插件
Package Control, Emmet, DockBlocker, SideBar, SideNav, Babel, ColorPicker
##### sublime无法输入中文解决办法
```bash 
* git clone https://github.com/lyfeyaj/sublime-text-imfix.git
* cd sublime-text-imfix
* ./sublime-imfix 
```
##### sublime下babel快捷emmet失效解决  
代码赋值至preferences -> Key bindings - Users:
```javascript
    {
  "keys": ["tab"], 
  "command": "expand_abbreviation_by_tab", 

  // put comma-separated syntax selectors for which 
  // you want to expandEmmet abbreviations into "operand" key 
  // instead of SCOPE_SELECTOR.
  // Examples: source.js, text.html - source
  "context": [
    {
      "operand": "source.js", 
      "operator": "equal", 
      "match_all": true, 
      "key": "selector"
    }, 

    // run only if there's no selected text
    {
      "match_all": true, 
      "key": "selection_empty"
    },

    // don't work if there are active tabstops
    {
      "operator": "equal", 
      "operand": false, 
      "match_all": true, 
      "key": "has_next_field"
    }, 

    // don't work if completion popup is visible and you
    // want to insert completion with Tab. If you want to
    // expand Emmet with Tab even if popup is visible -- 
    // remove this section
    {
      "operand": false, 
      "operator": "equal", 
      "match_all": true, 
      "key": "auto_complete_visible"
    }, 
    {
      "match_all": true, 
      "key": "is_abbreviation"
    }
  ]
},
```
### mongodb
```bash
* sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
* echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
* sudo apt-get update
* sudo apt-get install -y mongodb-org
```
### mongooBooster
> 一般情况下我使用图形化界面比较少，多数情况下使用命令行
```bash
* [下载软件-我的百度云](https://pan.baidu.com/s/1c1OhEnu)  
* chmod a+x *.AppImage   
* ./mon* // 启动
```
### markdown

[typora](https://www.typora.io/#)(特别好用，楼下特别难用):

```
# optional, but recommended
* sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
# add Typora's repository
* sudo add-apt-repository 'deb http://typora.io linux/'
* sudo apt-get update
# install typora
* sudo apt-get install typora
```



~~retext(特别好用) :~~

```bash
* sudo apt-get install retext 
卸载： 
* sudo apt-get remove retext
* sudo apt-get autoremove
```
(Ubuntu下sublime+markdown edit+markdown preview 不能实时刷新，需要每次保存打开刷新才能)  
### 有道词典
  [官网下载](http://cidian.youdao.com/index-linux.html):deb包双击就好啦
### 翻墙
* [lantern](https://github.com/getlantern/lantern)   
* [vultr](https://www.vultr.com/?ref=7359805)    
### gif录屏软件
> 待更新
### VIM打造IDE   
* [vim打造IDE](./vim.md)       
### docker   
* [dcoker](./dcoker.md)     
### Gimp   
* sudo add-apt-repository ppa:otto-kesselgulasch/gimp   
* sudo apt-get update   
* sudo apt-get install gimp   
* sudo apt-get install ppa-purge    
* sudo ppa-purge ppa:otto-kesselgulasch/gimp   
