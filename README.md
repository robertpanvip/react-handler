📦 **Installation**
``` javascript
npm install react-handler
```
🔨 **Usage**
``` javascript
/**demo1**/
import {OutSide} from 'react-handler';
function MyComponent() {
  return (
    <OutSide
      onOutSideClick={() => {
        alert('You clicked outside of this component!!!');
      }}
    >
       <span>Hello World</span>
    </OutSide>
  );
}

/**demo2**/
import {OutSide} from 'react-handler';
/**
 * FocusWithin  It's very similar to the Pseudo class :focus-within
 *
 * when you focus the input you will find the div will add class ‘is-focus’
 *and then when you blur you will find the div will remove class ‘is-focus’
 **/
function MyComponent2() {

  return (
    <FocusWithin>
       <div><input/></div>
    </FocusWithin>
  );
}

/**demo3**/
import {Handler} from 'react-handler';
/**
 * The function of the handler is to render not only children, but also click events in the proxy children
 * It is equivalent to rendering < div > {children} < / div > but deleting the div after the first rendering
 **/
function MyComponent3() {

  return (
    <Handler
      ref={(ref)=>{
        console.log('You will get the divs ref !!!');
      }}
      onClick={(e)=>{
         console.log('any event you can add to handler ');
      }}
    >
       <div>123</div>
    </Handler>
  );
}

```
🖥 **API**
###FocusWithin
``` javascript
interface FocusWithinProps {
    children: React.ReactElement;
    focusClassName?: string;
    disabled?: boolean;
}
export default class FocusWithin extends React.PureComponent<FocusWithinProps> {
    static defaultProps: {
        focusClassName: string;
    };
    render(): React.ReactNode;
}
```
###Handler
``` javascript
interface HandlerProps extends React.DOMAttributes<HTMLElement> {
    children: React.ReactElement;
    disabled?: boolean;
    onBeforeReplace?: (current: HTMLElement) => void;
    onAfterReplace?: () => void;
}
export default class Handler extends React.PureComponent<HandlerProps> {
    constructor(props: HandlerProps);
    render(): React.ReactNode;
}
```
###FocusWithin
``` javascript
interface OutSideProps {
    children?: JSX.Element;
    onOutSideClick?: (e: React.MouseEvent) => void;
    onClick?: (e: React.MouseEvent) => void;
    onMouseEnter?: (e: React.MouseEvent) => void;
    onMouseLeave?: (e: React.MouseEvent) => void;
    onFocus?: (e: React.FocusEvent) => void;
    onBlur?: (e: React.FocusEvent) => void;
    triggerTiming?: 'inner' | 'outside';
    once: boolean;
}
export default class OutSide extends React.Component<OutSideProps> {
    static defaultProps: {
        triggerTiming: string;
        once: boolean;
    };
    render(): React.ReactNode;
}
```
