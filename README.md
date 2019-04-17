###Mac 上使用pyenv 安装 python 3.5.0

1. 问题

    `pyenv install 3.5.0`
    
    如果出现以下错误
    ![]()        
    
    ```
    那好, 继续去搜索解决方法, 可能是找不到openssl的问题, 那么指定路径:
    CFLAGS="-I$(brew --prefix openssl)/include" \
    LDFLAGS="-L$(brew --prefix openssl)/lib" \
    pyenv install -v 3.5.0
    ```
    
    ```
    But, 还是出现以上问题, 接着搜索, 可能是openssl 的问题
    那么, 更新一下:
    brew upgrade openssl
    然后出新新的问题:
    ```
    
    ![]()

    
    ```
    OK, 继续搜索, 可能是brew 没有更新的问题:
    sudo chown -R $(whoami) /usr/local
    cd /usr/local/Library/Homebrew  
    git reset --hard  
    git clean -df
    brew update
    好了, 问题解决, 可以愉快的安装了    
    ```
    
2. 总结

    ```
    sudo chown -R $(whoami) /usr/local
    
    cd /usr/local/Library/Homebrew  
    git reset --hard  
    git clean -df
    brew update
    
    brew upgrade openssl
    
    CFLAGS="-I$(brew --prefix openssl)/include" \
    LDFLAGS="-L$(brew --prefix openssl)/lib" \
    pyenv install -v 3.5.0
    ```
    
3. 参考

    * [homebrew not working on OSX](https://stackoverflow.com/questions/24652996/homebrew-not-working-on-osx)
    * [I'm Getting Errors When I Try to do 'brew update'](https://apple.stackexchange.com/questions/231843/im-getting-errors-when-i-try-to-do-brew-update)
    * [mac下安装和使用brew](https://blog.csdn.net/fxp850899969/article/details/53284193)
    * [Common build problems](https://github.com/pyenv/pyenv/wiki/Common-build-problems)
    * [修复 pyenv 在 macOS High Sierra 上构建时的 ssl 依赖问题](https://www.v2ex.com/t/397232)
    
    
    


