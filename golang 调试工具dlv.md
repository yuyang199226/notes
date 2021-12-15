# 安装

gilang 1.16版本

`go install github.com/go-delve/delve/cmd/dlv@latest`

使用

新建一个go 文件

```
package main
import "fmt"

func sum(a, b int) int {
        return a+b
}

func main() {
        a := 1
        b := 3
        c := sum(a,b)
        fmt.Println(c)


}
```

## dlv debug 使用

执行dlv 命令,进入到dlv 命令里

`dlv debug main.go`


```
(dlv) list main.go:5  # 显示文件某一行
(dlv) b main.go:10    # 给这一行打断点
(dlv) c               # 继续运行程序
(dlv) locals          # 打印局部变量
(dlv) p a             # 打印变量 a 的值
(dlv) set a = 2       # 改变变量 a 的值
(dlv) b main.go:12    # 接着打断点
(dlv) p c             # 打印变量的值
(dlv) breakpoints     # 查看断点
(dlv) clear 1         # 清除第一个断点
(dlv) clearall        # 清除所有断点
(dlv) c               # 继续运行
(dlv) r               # 重启进程
(dlv) q               # 退出dlv
``` 

## dlv exec 的使用
dlv exec 后面跟可执行的二进制文件
需要注意的是如果要加断点，需要在编译的时候加这上参数 `-gcflags="-N -l"`

```
go build -gcflags="-N -l" main.go
dlv exec ./main # 进入dlv 窗口
(dlv) 
```

# 参考
- https://github.com/go-delve/delve/blob/master/Documentation/cli/getting_started.md
- https://pytimer.github.io/2018/06/go%E8%B0%83%E8%AF%95%E5%B7%A5%E5%85%B7delve/
