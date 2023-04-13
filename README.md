# componentLibray

组件库

```
import { GlobalTheme, Utils } from 'tuya-panel-kit';
import { DeepPartial } from '@utils';
import { Platform } from 'react-native';

const { get } = Utils.CoreUtils;
const { convertX: cx, convertY: cy } = Utils.RatioUtils;

export const getBrandColor = (props: GlobalTheme) => {
  const type = get(props, 'theme.type', 'wiser');
  const path = ['theme', 'global', 'brand', type].join('.');
  return get(props, path, '#008A16');
};

const normalizeFont = (props, fontSize, lineHeight, bold = false) => {
  const baseline = get(props, 'theme.global.fontSizeBase', 1);
  return {
    fontSize: cx(fontSize * baseline),
    lineHeight: Math.round(cx(lineHeight * baseline)),
    fontWeight: bold ? '600' : '400',
  };
};

const DIALOG_BACKGROUND_COLOR = '#fff';

const DIALOG_STYLE = {
  color: '#000',
  backgroundColor: DIALOG_BACKGROUND_COLOR,
  shadowOffset: { width: 0, height: 4 },
  shadowOpacity: 0.25,
  shadowColor: '#000',
  shadowRadius: 8,
  elevation: 40,
};

export default {
  type: 'wiser', // wiser | elko
  global: {
    brand: {
      wiser: '#008A16',
      elko: '#D70929',
    }, // 品牌色（主题色） y
    bgColor: '#fff', // 背景色
    background: '#eee', // 背景 y
    fontSizeBase: 1, // 字体基准比例
    dividerColor: '#D9D9D9', // 分隔线颜色 y
    success: '#008A16', // 成功颜色
    warning: '#FAAE17', // 警告颜色
    error: '#ED2B00', // 失败 y
    mask: 'rgba(255, 255, 255, 0.9)', // 遮罩颜色 y
    text: '#000',
    fontFamiily: 'nunito',
  },
  // 主题色
  color: {
    primary: getBrandColor,
  },
  // 文案颜色 y
  fontColor: {
    primary: '#000',
    secondary: '#333',
    tertiary: '#626469',
    contrast: '#fff',
    error: '#ED2B00',
    link: '#1772ED',
  },
  // 文字
  text: {
    title: {
      extraLarge: (props: any) => normalizeFont(props, 34, 40, true),
      large: (props: any) => normalizeFont(props, 28, 34, true),
      normal: (props: any) => normalizeFont(props, 22, 28, true),
      small: (props: any) => normalizeFont(props, 17, 22, true),
    },
    subTitle: {
      nomal: (props: any) => normalizeFont(props, 17, 22),
      small: (props: any) => normalizeFont(props, 15, 20),
    },
    paragraph: {
      highlight: (props: any) => normalizeFont(props, 17, 17, true),
      normal: (props: any) => normalizeFont(props, 17, 17),
      small: (props: any) => normalizeFont(props, 15, 15),
    },
    footNote: {
      large: (props: any) => normalizeFont(props, 13, 16, true),
      normal: (props: any) => normalizeFont(props, 13, 16),
      small: (props: any) => normalizeFont(props, 12, 16),
    },
  },
  // 顶部栏
  topbar: {
    background: 'transparent',
    color: '#000',
  },
  button: {
    fontColor: '#fff',
    // 实心按钮
    brick: {
      bgColor: getBrandColor,
    },
    // 线框按钮
    plain: {},
    // 文案按钮
    link: {},
  },
  // 开关按钮
  switchButton: {
    width: cx(42), // 按钮宽度
    height: Platform.select({
      // 按钮高度
      web: 22,
      ios: 22,
      android: 22,
    }),
    thumbSize: cx(18), // 滑块宽高尺寸
    margin: Platform.select({
      // 滑块四周边距
      web: 0,
      ios: 0,
      android: 0,
    }),
    tintColor: '#E6E6E6', // 关闭情况下背景色
    onTintColor: '#008A16', // 开启情况下背景色
    thumbTintColor: '#fff', // 关闭情况下滑块背景色
    onThumbTintColor: '#fff', // 开启情况下滑块背景色
  },
  slider: {
    trackRadius: 2, // 滑块圆角
    trackHeight: 4, // 滑块高度
    minimumTrackTintColor: '#979797', // 最小值颜色
    maximumTrackTintColor: '#333', // 最大值颜色
    thumbSize: 24, // 滑块圆的尺寸
    thumbRadius: 14, // 滑块圆的圆角
    thumbTintColor: '#fff', // 滑块的颜色
  },
  // 弹窗
  dialog: {
    width: cx(315), // 弹窗容器宽度
    bg: DIALOG_BACKGROUND_COLOR, // 弹窗背景色
    radius: cx(8), // 弹窗容器圆角
    cellHeight: 56, // 列表高度（头部、底部）
    lineColor: '#000', // 分隔线颜色
    titleFontSize: 18, // 标题字体大小
    titleFontColor: '#000', // 头部栏标题颜色
    subTitleFontSize: 16, // 副标题字体大小
    subTitleFontColor: '#000', // 头部栏副标题颜色
    cancelFontSize: 16, // 底部栏取消字体大小
    cancelFontColor: '#666', // 底部栏取消字体颜色
    confirmFontSize: 16, // 底部栏确认字体大小
    confirmFontColor: getBrandColor, // 底部栏确认字体颜色
    ...DIALOG_STYLE, // 通用弹窗阴影
    prompt: {
      bg: '#f8f8f8', // 输入框背景色
      radius: cx(4), // 输入框圆角
      padding: '12px 16px', // 输入框边距
      placeholder: '#d6d6de', // 占位符字体颜色
    },
  },
  navigator: {
    bg: '#f7f7f7',
    selectedColor: '#fff',
  },
  layout: {
    space: cx(16),
  },
} as DeepPartial<GlobalTheme>;
```
