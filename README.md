# V1.1
## 开发环境
基于 *[乐鑫esp-idf v4.3.2](https://github.com/espressif/esp-idf/tree/v4.3.2)* 开发 兼容V4.3.1  
Docker镜像 docker push shukewt/esp-idf:v4.3.1  

## 选择开发板  
使用load.sh加载开发板配置  
 `bash load.sh`  
当前支持型号  
1): WT32_SC01_LANDSCAPE  
2): WT32_SC01_PORTRAIT  
3): WT154-S2MI1-PERFORMANCE  
4): WT154-S2MI1-WIFI  
5): WT154_C3SI1  
6): WT-86-32-3ZW0-PERFORMANCE  
7): WT-86-32-3ZW0-WIFI  
8): WT-86-32-3ZW1-PERFORMANCE  
9): WT-86-32-3ZW1-WIFI  
10): WT280-S2MT1  
11): WT280-S2MI1  

## 新特性
- 使用8ms平台进行UI开发的用户请将source.zip内容替换至 components/qmsd\_ui 目录
- 由于8ms生成的UI部分代码不再开放编辑，需要自定义UI交互请使用8ms自定义回调相关blockly指定需处理的事件，相关事件处理参考工程main/control/qmsd\_ui\_cb.c 中代码开发，UI相关元素获取可以参考 components/qmsd\_ui/ui/qmsd\_ui\_entry.h 中声明的相关get方法  
- qmsd\_ui\_cb.c中的 qmsd\_ui\_cb 函数运行在UI线程内部，因此不建议在其中执行阻塞或延时，需要异步任务可以参考main/control/qmsd\_control.c 中定义的事件收发与处理
- 在UI线程以外的外部线程中直接操作UI相关内容可能会造成不同程度的异常，因此在components/qmsd\_init/qmsd\_ctrl.h中提供了在保证线程安全情况下进行UI操作的相关api 其中的操作协议可以参考8ms开发文档*[控制协议](http://doc.8ms.xyz/docs/gui/gui-1dgqjgc2de1lk)*章节

