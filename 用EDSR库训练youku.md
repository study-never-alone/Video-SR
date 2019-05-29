### 需要修改的参数
data_range: 分割训练集和测试集的长度。 针对20000张图片我们设置为： 1-19000/19000-20000
--data_train: YOUKU
data_test:YOUKU
model:模型类型
ext:'img' 防止序列化，不然空间不够。
precision："half" "single"官方文档中是test的类型？仅仅是test时候吗。 感觉没啥用
no_augment: "store_true"是否采用增广度（随机翻转和旋转）

继续训练需要的参数：
pre_train：与训练模型位置
resume：继续训练

待解决：
batch_size: n_patches = args.batch_size * args.test_every
test_every
--print_every:默认100，100个batch显示一次。

'--load', type=str, default='',
                    help='file name to load'

parser.add_argument('--resume', type=int, default=0,
                    help='resume from specific checkpoint')


## 训练记录

1. 默认EDSR，数据bmp，一视频100帧.LOSS:1.0*L1
```
python main.py --model EDSR --scale 4 --patch_size 96 --save edsr_baseline_x4_youku --reset --dir_data F:\ --data_train YOUKU --data_test YOUKU --ext img --data_range 1-19000/19000-20000
```
资源占用：1G内存

2. RCAN训练
batch_size=32
```
python main.py --template RCAN --save RCAN_BIX4_G10R20P48 --scale 4 --reset --patch_size 96 --dir_data F:\ --data_train YOUKU --data_test YOUKU --ext img --data_range 1-19000/19000-20000
```