插件
====

Blink 0.3 引入插件的概念, 通过提供轻量级的插件机制支持, 我们可以在应用启动阶段向应用程序注入代码, 比如动态的注册服务、添加路由。
通过这样的插件机制, 我们可以实现如下目标:

1. 我们可以实现自组织的模块, 将一个大的项目拆解成为一个个小模块。
2. 实现代码复用, 将公共代码封装成插件, 不同的 Blink 项目共用


## 实现一个插件

要实现一个 Blink 插件非常简单, 我们只需要实现 `blink\core\PluginContract` 接口就行了, 这个接口只有一个 `install()` 方法, 其会在应用
启动阶段调用, 可以在这个方法内做一些插件初始化的工作, 比如注册服务, 添加路由。

## 安转一个插件

插件的安装遵循 Blink 统一的配置方式, 默认我们只需要在 `src/config/plugins.php` 添加对应的插件配置就行了, 比如:

```
return [
    'plugin1' => [
        'class' => 'namespace/to/Plugin1Class',
        'prop1' => 'prop1',
    ],   
];
```
